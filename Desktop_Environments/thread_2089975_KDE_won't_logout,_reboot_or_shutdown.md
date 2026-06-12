---
title: "KDE won't logout, reboot or shutdown"
date: 2012-11-30
forum: Desktop Environments
---

### Post by cat2005 on 2012-11-30
Sometimes KDE won't logout, reboot or shutdown when I go to the proper menu.

How do I fix this?  

Using KDE 4.8.5 on 64bit Ubuntu 12.04

---

### Post by 2F4U on 2012-11-30
When that happens have you tried to reboot or shutdown through a terminal, and did that produce the desired result?

---

### Post by cat2005 on 2012-12-01
> **2F4U said:**
> When that happens have you tried to reboot or shutdown through a terminal, and did that produce the desired result?

Unfortunately I don't know much about terminal.  I was in my non-root account.  I tried the following in terminal but got the reply that I needed to be root.

shutdown -h now
reboot -h now

I assume my syntax is correct but like I said, I don't know that much about command line.  I always manually reboot when this happens.

---

### Post by SantaFe on 2012-12-01
Just add sudo to the front of either command while in the Terminal window.

I.E.

sudo shutdown -h now
sudo reboot -h now

Although you really can replace the bottom one with Sudo shutdown -r now.  Think it does the same thing.

---

### Post by slixz85 on 2013-01-27
reinstall the package menu-xdg or install it if it is not installed. this is the one that has the reboot shutdown options

---

