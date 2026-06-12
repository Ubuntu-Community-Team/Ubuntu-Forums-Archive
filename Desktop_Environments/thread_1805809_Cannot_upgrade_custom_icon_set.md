---
title: "Cannot upgrade custom icon set"
date: 2011-07-16
forum: Desktop Environments
---

### Post by ratcheer on 2011-07-16
I am using Natty in Classic Gnome mode with a custom icon set, Awoken. It is doing fine, but an upgrade was released a few days ago and the installation fails:

```
Preparing to replace awoken-icon-theme 2.0~ppa1~natty2 (using .../awoken-icon-theme_2.1~ppa1~natty1_all.deb) ...
Unpacking replacement awoken-icon-theme ...
dpkg: error processing /var/cache/apt/archives/awoken-icon-theme_2.1~ppa1~natty1_all.deb (--install):
 unable to open '/usr/share/icons/AwOken/clear/24x24/drive-harddisk/USB-HD.png.dpkg-new': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/awoken-icon-theme_2.1~ppa1~natty1_all.deb
```There is a page for awoken-icon-theme package on Launchpad, but I cannot  find a way to submit a bug on it. If I try "ubuntu-bug  awoken-icon-theme", it is rejected because it is not an Ubuntu package. I  understand that. Should I try to contact the developer directly?

How can I resolve this error and get the upgrade installed?

Thank you,
Tim

---

### Post by koleoptero on 2011-07-16
I have the same thing and I've set it to hold the update till I know it's fixed. :(

---

### Post by LoGinthebest on 2011-08-02
do sudo apt-get remove awoken-icon-theme

and then

sudo apt-get install awoken-icon-theme

That worked for me...

---

### Post by ratcheer on 2011-08-02
Thanks, LoGinthebest. I'll try that.

Tim

---

