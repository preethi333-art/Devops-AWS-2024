`useradd` and `adduser` are both used to create user accounts in Linux, but they differ in how they work.

| Feature        | `useradd`                                   | `adduser`                                       |
| -------------- | ------------------------------------------- | ----------------------------------------------- |
| Type           | Low-level command                           | High-level interactive script                   |
| Interactivity  | Non-interactive                             | Interactive                                     |
| Home directory | May not create one unless `-m` is used      | Creates home directory by default               |
| Password       | Doesn't ask for password                    | Prompts to set password                         |
| User details   | Doesn't ask for full name, phone, etc.      | Prompts for additional user information         |
| Ease of use    | More options, suited for scripting          | Easier for beginners                            |
| Availability   | Available on almost all Linux distributions | Mainly available on Debian/Ubuntu-based systems |

### `useradd`

Creates a user with minimal configuration.

**Example:**

```bash
sudo useradd preethi
```

This only creates the user. It **does not**:

* Create a home directory (unless `-m` is used)
* Set a password
* Ask for user information

To create a complete user:

```bash
sudo useradd -m -s /bin/bash preethi
sudo passwd preethi
```

Here:

* `-m` → Create `/home/preethi`
* `-s /bin/bash` → Set the default shell
* `passwd` → Set the user's password

---

### `adduser`

`adduser` is a user-friendly wrapper around `useradd`.

**Example:**

```bash
sudo adduser preethi
```

It automatically:

* Creates the home directory
* Creates a user group
* Copies default files from `/etc/skel`
* Prompts for a password
* Asks for optional information (Full Name, Room Number, Phone, etc.)

Example interaction:

```text
Adding user `preethi' ...
Adding new group `preethi' ...
Adding new user `preethi' (1001) with group `preethi' ...
Creating home directory `/home/preethi' ...
Copying files from `/etc/skel' ...
New password:
Retype new password:
Full Name []:
Room Number []:
Work Phone []:
Home Phone []:
Other []:
Is the information correct? [Y/n]
```

---

### Which should you use?

* Use **`adduser`** when creating users manually on Ubuntu/Debian. It's simpler and safer.
* Use **`useradd`** in automation scripts or when you need precise control over user creation options.

### Quick Summary

| Command              | Best Use                                     |
| -------------------- | -------------------------------------------- |
| `adduser preethi`    | Manual user creation (recommended on Ubuntu) |
| `useradd -m preethi` | Scripts and automation                       |
| `passwd preethi`     | Set or change the user's password            |

**Remember:** `adduser` is essentially a friendly front-end that internally uses `useradd` with appropriate options and additional setup.
