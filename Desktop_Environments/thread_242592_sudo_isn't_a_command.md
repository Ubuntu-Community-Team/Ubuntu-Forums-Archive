---
title: "sudo isn't a command?"
date: 2006-08-23
forum: Desktop Environments
---

### Post by buyj3llo on 2006-08-23
okay, I've been going through all of this "xserver" drama for a while. I found the directions on how to fix it on the front page. I tried to do this:```
sudo apt-get upgrade
```but it keeps telling me this:```
bash: sudo: command not found
```
:confused: 
what's going on? Am I doing something wrong? I'm pretty much a linux noob so I'd really apreaciate it if you can dumb it down to my level.

---

### Post by mlind on 2006-08-23
Hopefully you haven't uninstalled sudo package somehow :confused: 
What's the ouput of **whereis sudo** ? Also, try invoking /usr/bin/sudo.

If sudo binary is not in /usr/bin, then you need to boot into recovery mode (from GRUB menu) and install sudo package back as root.

---

