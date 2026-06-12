---
title: "All I can see is a brown screen and a mouse pointer"
date: 2009-02-06
forum: General Help
---

### Post by declank on 2009-02-06
Installed ubuntu-8.10-desktop-i386.iso

All I can see is a brown screen and a mouse pointer

All indications are buggy Compiz code used by Gnome in screen candy and special effects. What's happening is linux boots successfully, Xwindows comes up fine, Gnome using Compiz builds the desktop image, then some code I assume Compiz hangs up altogether.

Going to try Ubuntu 8.04.2 LTS (Hardy Heron) to see if this fixes the issue but would hate to think its the end of the road for Ubuntu on my IBM R31.

---

### Post by markharding557 on 2009-02-06
try disabling or removing compiz

---

### Post by meinvateristnein on 2009-02-06
i aggree with him you must disable compiz and compiz core because your video hardware is to crappy or the correct drivers werent installed ....... 

code: sudo apt-get remove compiz
sudo apt-get remove compiz-core 


to type this code in simply start up computer when grub loads press Esc and goto 3rd option down this will allow you to remove these terrible ubuntu software options

---

### Post by declank on 2009-02-06
As you said... fixed with:

sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume
then boots to Gnome desktop. After removal, then the install just normally boots to desktop O.K.


[https://bugs.launchpad.net/ubuntu/+bug/259385](https://bugs.launchpad.net/ubuntu/+bug/259385)


And yes the graphics card probably is crappy  :p

---

### Post by Yashiro on 2009-02-06
You get this when your video card reports it can do composite but the 3d portion of the driver is not activated properly. 
Be it from a bad driver or borked install. 
It's common to Ati cards when *fglrx* is **not** blacklisted in /etc/modprobe.d/local-blacklist. ie it should contain '# blacklist fglrx' for proper acceleration.

What hardware do you have?

Try booting up.
When it blanks out. Press Alt+F2.
Type Xterm, enter.
Type metacity --replace, enter.
Go into appearance settings and disable effects till you sort the driver issue out.

---

