---
title: "debian buster netinstall doesn't let me apt-get update"
date: 2020-12-12
forum: Debian
---

### Post by onlineaddy on 2020-12-12
I installed a netinstall.iso of the latest Debian 10.7 Buster. Everything went well during the installation, I configured my wifi, selected my local country mirror for the updates, the installer downloaded everything but after a reboot and login I can't update apt. I continually get some errors ("failed to fetch.." or "some infex files failed to download". What can I do to fix this? 

I already tried editing sources.list with the official Debian Buster info, but I still get the same error, can't connect. Even if I plug in cable internet in my laptop. 

Could anyone help? Thank you.

```
# apt-get update
Err:1 http://deb.debian.org/debian buster InRelease
Temporary failure resolving 'deb.debian.org'

```

---

### Post by CelticWarrior on 2020-12-12
"[COLOR=#000000][FONT=&quot]Temporary failure resolving 'deb.debian.org'" suggests a DNS problem.
[/FONT][/COLOR]

---

### Post by ajgreeny on 2020-12-12
Let's see the what the content of your /etc/apt/sources.list now is with the output of terminal command ```
cat /etc/apt/sources.list
```
What were the edits you made to the file?
Do you actually have an internet connection; are you using the debian install to write this forum post/thread?
Does the rest of the system appear to work correctly?

---

