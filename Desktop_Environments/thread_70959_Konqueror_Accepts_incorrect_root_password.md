---
title: "Konqueror Accepts incorrect root password"
date: 2005-10-01
forum: Desktop Environments
---

### Post by mendebrock on 2005-10-01
A problem that I ran across when I installed Kubuntu this afternoon. As you know, the root account is disabled by default. I worked with the system in this configuration for a while but eventally decided that I'd rather have the root account active.

Some time (and several reboots) after I activated the root account, I tried to edit a restricted file (/etc/apt/sources) using the actions shortcut within Konqueror and was surprised when it didn't accept the root password. After several attempts, I supplied my user account password and was equally surprised when Kate opened the file in edit mode. I was able to make the changes I wanted and save them. Hmmmmmm......seems like a security problem to me.

Am I missing something here, or is this a genuine security hole in the system?

---

### Post by aysiu on 2005-10-01
On a default install, there is no root or root password. Read more here:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

