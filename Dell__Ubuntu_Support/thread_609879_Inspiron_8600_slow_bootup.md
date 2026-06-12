---
title: "Inspiron 8600 slow bootup"
date: 2007-11-11
forum: Dell  Ubuntu Support
---

### Post by Jiganto on 2007-11-11
Hi,

This is a new issue that I've encountered that I haven't had with previous Ubuntu installations. 

I did a clean install of 7.10 yesterday with a CD I got in the mail. The issue I'm having is an very slow boot up. 

Upon starting, right after the "Starting up..." terminal looking window, the the screen just blanks out, and stays like that for a good two minutes. No loading screen of any sort appears, and it stays like this until the login screen finally loads. At first I thought nothing was happening, until in low light I still saw that the back-light was on. 

Prior to 7.10 the laptop would boot up in about 30 seconds. 

The laptop has 768mb of ram, Pentium M processor, and a 128mb Radeon 9600 pro-turbo video card. 

Any advice on how I can go about resolving this would be much appreciated.

Thanks

---

### Post by Jiganto on 2007-11-12
bump

---

### Post by Dellfan on 2007-11-12
You may be having an issue with it detecting your graphics card and resolution. Check and see if /etc/usplash.conf has sane resolution data. Another suggestion is to:

Make a copy of the Grub menu.lst found in /boot/grub/

Now, find the line that reads along the lines of:

kernel  /boot/vmlinuz-2.6.22-14-generic root=/dev/hda3 ro splash quiet

and remove the "splash" and "quiet" and see what that does to your boot time.

---

### Post by Jiganto on 2007-11-13
It was an issue with the usplash.conf. The resolution was set incorrectly.

Thanks for the help.

---

