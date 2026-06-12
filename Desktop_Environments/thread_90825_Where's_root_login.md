---
title: "Where's root login ??"
date: 2005-11-15
forum: Desktop Environments
---

### Post by dbee on 2005-11-15
I just switched from hoary and I can' t find the bash root  terminal anywhere.

Actually, I can't even find the non-root bash terminal ... pls tell me ubuntu hasn't done a windowsXP and left out the command line ???? That couldn't be true ... :confused:

---

### Post by teaker1s on 2005-11-15
applications-system tools-konsole

---

### Post by 23meg on 2005-11-15
The terminal is in Applications / System Tools. Prefer [sudo]("https://wiki.ubuntu.com/RootSudo") to logging in as root. If you absolutely must become root, set a root password with "sudo passwd root" and then type "su" in the terminal and enter the root password you set.

---

### Post by dbee on 2005-11-15
cool,

the terminal was hidden by default, I just enabled it again ... panic over !

I can't find the non-root terminal though ... but anyway, I'm wondering 23meg besides the obvious, what's the advantage of using sudo instead of just issuing command at root.

---

### Post by 23meg on 2005-11-15
You'll find out if you check out the link I posted above.

---

