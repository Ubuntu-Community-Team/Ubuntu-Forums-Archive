---
title: "The program 'grub' is currently not installed"
date: 2010-12-18
forum: Desktop Environments
---

### Post by nluna-wi on 2010-12-18
Noobie here.  Please help.  I would like to know if I should install GRUB 2

I wanted to check what version of GRUB I have installed.  I went to terminal and typed
grub --versionI got this message back:

The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub

I am running Ubuntu 10.10 alongside windows xp pro.  When I turn my pc on I have the option to boot to ubuntu or xp and at the top of the window it says that the version of grub running is "GNU GRUB Version 1.98+20100804-5Ubuntu-3"  Please let me know how I shold go about installing GRUB 2 or just leave it as is.  Thanks in advance.

---

### Post by hhh on 2010-12-18
That version is Grub2, leave it alone.

-edit- more info...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by sikander3786 on 2010-12-18
The default Grub loader that comes with Ubuntu > or = 9.10 is codenamed Grub2 but actually it is Grub 1.98. Search Synaptic for grub-pc and you'll find more.

And that will be automatically updated via Update Manager. You don't need to update anything manually.

Important: Have you install Ubuntu inside Windows using the Wubi installer? If yes, you might not want to upgrade that as it is likely to break the whole system.

See the section named 'Permanent Fix' here.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

And if it is a proper install and not Wubi, you don't need to worry about anything else.

---

