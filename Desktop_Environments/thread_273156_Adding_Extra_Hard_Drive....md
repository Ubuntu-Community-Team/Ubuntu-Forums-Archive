---
title: "Adding Extra Hard Drive..."
date: 2006-10-07
forum: Desktop Environments
---

### Post by Billsey on 2006-10-07
Can someone tell me how I can go about adding a second internal hard drive and actually be able to use it under Ubuntu?

I am now reinstalling Ubuntu after my efforts to get that second hard drive to mount as read/write without me having to be the root user in order to use the thing resulted in a scotched install.

I am expanding into Linux from the Mac world, and adding a second internal hard drive that is actually usable by the guy that owns the computer does not need to be so mind-numbingly difficult to accomplish.

I mean come on. On Mac, you plug in the hard drive, reboot, it's there—and you can actually use it. With all the brain power involved in the Linux/Ubuntu world why is that not the case with Ubuntu?

I am new here, so I'm probably missing something, but it escapes me why a Linux system that does not include the root user would set up new hard drives so that only the root user can access them.

Please illumine me.

---

### Post by catlett on 2006-10-07
If you have issues with permissions, all you have to do is change the permissions through the right-click options menu as root.
To launch the file manager as root, use gksudo 
```
gksudo nautilus
```Then browse to the file/directory that you want to change permissions. Right click on the file to bring up the options menu. Select "properties", this will open a window. In the window, select the "properties" tab. Checking off the boxes will change the permissions. Since you are root, you can change the permissions to allow all users and groups to use the file. (if you have other people using the compuiter you may not want to do this but if it is just you, it doesn't matter).
Ubuntu is free and not meant to compete with commercial OS's like OSX and XP, it is a philanthropic project by Mark Shuttleworth to allow third world and poor industrial people the ability to use a computer. You may be better off paying for a linux distro so you do not have to be bothered with these little "issues" that come with a free OS. The 'friendliest' distro is Xandro's. For $70 you get a complete esy to use system and the best user's guide ever written for a distro. You can get it here [http://www.xandros.com/products/products.html](http://www.xandros.com/products/products.html)

---

### Post by confused57 on 2006-10-07
Maybe this website can help, see the section "Mount Linux":
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

