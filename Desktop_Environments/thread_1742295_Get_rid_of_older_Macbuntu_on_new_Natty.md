---
title: "Get rid of older Macbuntu on new Natty"
date: 2011-04-28
forum: Desktop Environments
---

### Post by hashcode on 2011-04-28
Today I upgraded to Natty, but I can't uninstall Macbuntu from my older 10.10 (it just says that I have incompatible version ;(

Here are few problems:

1. How can I change default theme (say to Ambiance) of login screen?
2. How can I remove weird apple logo when booting (I think it has something to do with grub)

thx

---

### Post by Krytarik on 2011-04-28
Please see my earlier post regarding those, it applies to Natty, too:
[http://ubuntuforums.org/showthread.php?p=10468340#post10468340](http://ubuntuforums.org/showthread.php?p=10468340#post10468340)

The default Plymouth splash theme is "ubuntu-logo".

Greetings.

---

### Post by deconstrained on 2011-04-28
2. If you're using plymouth to display your splash animation, you can use 'update-alternatives --config plymouth.default' to change it. Then run 'update-initramfs -u' to apply the changes.

---

### Post by hashcode on 2011-04-29
I have removed apple logo like this:

**sudo update-alternatives --config default.plymouth**

---

### Post by hashcode on 2011-04-29
I have changed login theme like this:

[http://www.techytalk.info/2011/02/ubuntu-debian-gdm-login-screen-theme-wallpaper/](http://www.techytalk.info/2011/02/ubuntu-debian-gdm-login-screen-theme-wallpaper/)

---

