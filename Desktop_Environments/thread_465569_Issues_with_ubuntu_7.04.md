---
title: "Issues with ubuntu 7.04"
date: 2007-06-05
forum: Desktop Environments
---

### Post by Magiczero on 2007-06-05
Hi

I am posting this message to try to get help with my laptop.  The laptop is a Dell inspiron 2500 with ubuntu 7.04.  I am having a few issues with ubuntu.  Just to give you a little background info, these issues began when I first put ububry on the laptop.  The live/installer CD did not work on the Inspiron 2500.  I had to use the Alternative CD and do a text-based installation of ubuntu.  

Here are my problems that I am having

1.No Splash On Startup or shutdown
I have no splash on startup or shutdown since I installed Ubuntu 7.04
I tried different commands to fix the splash
sudo cat /boot/grub/menu.lst
cat /etc/X11/xorg.conf
Those commands did not change anything
I tried more commands
sudo gedit /boot/grub/menu.lst
I added this line to the file
2.kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=e0e37017-1b07-48b9-a965-7d01c5bb50f1 ro quiet splash vga=791
3.Then I added another line to the file
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=e0e37017-1b07-48b9-a965-7d01c5bb50f1 ro quiet splash
Saved the file & rebooted, Nothing changed still no splash

Problem 2:  800 x 600 resolution
Everything is really big!  

The laptop is running at 800 x 600 and everything is really big and when I change it to 1024 x 768 everything is even bigger.  

Problrm 3:  When the laptop starts up after it gets past the GRUB screen & the Ubuntu splash I have to hit FN F7 for it to show anything on the screen  Why do I have to do this?
I am not a noob I have been urning ubuntu on a desktop foe 2 years & love it!!
Could most of these issues be a driver issue?
Any answers to any of my questions?

Thanks

---

### Post by Wherdgo on 2007-06-06
Still a known bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442)

---

