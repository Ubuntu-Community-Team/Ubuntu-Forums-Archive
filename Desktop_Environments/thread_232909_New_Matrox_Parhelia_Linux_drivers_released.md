---
title: "New Matrox Parhelia Linux drivers released"
date: 2006-08-09
forum: Desktop Environments
---

### Post by drucer on 2006-08-09
Hi, there's been a lot of discussion about Matrox Parhelia Linux drivers in the past. Matrox has released new official Parhelia/EPICA Linux display drivers just a couple of weeks ago. Driver version number is 1.4.4 and 64bit platforms are also supported for the first time.

[http://forum.matrox.com/mga/viewtopic.php?t=20813](http://forum.matrox.com/mga/viewtopic.php?t=20813)

So, the question is. How can one install these drivers on Ubuntu Linux? I'm sure there are people who have done it. At least compiler tools are needed. Please share your information with the rest of us. It would also be nice if these drivers were included with Ubuntu when the next version is released. Suse, Redhat and some others will start supporting Matrox Parhelia cards out of the box now.

---

### Post by leech on 2006-09-24
I currently no longer have a Matrox Parhelia card.  But I actually was the original one who discovered the easiest method of installing it on a Debian based system, and I doubt that it actually has changed a whole lot.

All you really need to do is 'sudo apt-get install module-assistant'

Then run 'sudo module-assistant' and select "prepare" this will download all the packages that you will need to create any modules for your kernel.  Plus it will also create the proper symbolic links, etc.

Then you would just run the script (can't recall what it is, but generally something like mtx-install.sh, so you would run it 'sudo sh mtx-install.sh)

After that, simply edit /etc/X11/xorg.conf with your favorite text editor (I like nano myself, so something like 'sudo nano /etc/X11/xorg.conf') and change your video driver (probably already set to vesa) to mtx.  Final step is to edit /etc/modules and add 'mtx' to the bottom of the list there.  Then you can either reboot, or log out, then hit control+alt+F1, login at the console, then type 'sudo modprobe mtx' and finally 'sudo /etc/init.d/gdm restart'

After that you should get a Matrox splash screen and hopefully everything should work fine.

Leech

---

### Post by drucer on 2006-09-24
Great! Thank you very much for these instructions! This will help many people out there (me included).

---

