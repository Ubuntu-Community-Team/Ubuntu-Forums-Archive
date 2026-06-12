---
title: "I Need A small bit of help please :)"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by deadwalkin on 2007-04-26
OK I have 2 problems first one is i have download the new ubuntu desktop and your new cube dont work is there some thing i can do to fix this the wobble works but not the cube,
if you r on the live cd it works great. but not when its installed.
any ideas be nice
also i have ubuntu runing on a samsung V25 laptop and screen res will not change to 1024x
any help on these isuse's will be great and Ubuntu rules still,

---

### Post by orange2k on 2007-04-26
To enable the cube, read here: [http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367)

To enable additional resolutions you can try the following command in the console:

sudo nano /etc/X11/xorg.conf

Scroll down until you find the section "Screen".
All resolutions available to you will be listed so just add the resolutions you want for every
screen depth. At the end save the file with ctrl+o, reboot and you`re done...

---

