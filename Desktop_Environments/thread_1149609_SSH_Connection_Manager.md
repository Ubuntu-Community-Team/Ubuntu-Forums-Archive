---
title: "SSH Connection Manager"
date: 2009-05-05
forum: Desktop Environments
---

### Post by bradlis7 on 2009-05-05
I work in an environment that requires a lot of remote connections to different servers. I was creating a small PyGTK program that manages the hosts and allows the user to SSH in, but would also like the program to be able to SFTP in using nautilus. I don't want to mess with keys, but I would like to be able to store the password to use in both SSH and SFTP. I solved the SSH connection problem by using an expect script, but passing the password to nautilus does not seem possible.

We also have other connection types (telnet, etc), as we work with Cisco routers and other devices.

One option to be able to use passwords between the programs, I could write my program to use gnome-keyring to manage the passwords. Does anyone else have any recommendations?

---

