---
title: "blank desktop after login"
date: 2009-04-20
forum: Desktop Environments
---

### Post by Eric B on 2009-04-20
Hi.

I get my Gnome login screen, and when I log in, I get a blank blue background with nothing else. Then a grayish box appears in the upper left corner. If I put the cursor in that area, it turns into a text selection cursor. 

I tried logging into failsafe, but I get the same results. I also tried ```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
``` in hopes of resetting gnome. I still get the same results. Any idea what else I can try?

---

### Post by Big Luke on 2009-04-20
Well, I am no expert but I have run into that "type of situation" before.  I may be able to lend some assistance but it all depends on how far you are willing to go.

If it were me, I would boot to the Live CD, mount the partition in order to gain access to files i may want to back up to a different computer, external HD, etc.  And then I would completely reinstall ubuntu.  

I will mention this just in case you have not done it already, it saves you a headache or two if you find yourself in need of reinstalling a OS, but keeping files.  Do you have 2 separate Ubuntu partitions, one mounted as / and one as /home???  there are several advantages to this, if you are going to install a new OS, you can just format the partition mounted as / and mount the /home partition.  Also if you get into a situation like this again you can just reinstall ubuntu straight away.

---

### Post by Eric B on 2009-04-20
Yes, I went partition crazy. I have several for different mount points. I would have to reinstall a bunch of apps though, and I dont really feel like doing so at the moment. Not if there is an easier solution. I can use this old Windows desktop in the meantime.

---

### Post by Eric B on 2009-04-21
Any thoughts besides a reinstall?

---

### Post by anants on 2009-04-21
Eric,

Please try:

1. reinstall gnome desktop 
[sudo apt-get remove --purge gnome-desktop-environment
[sudo apt-get install gnome-desktop-environment]

2. restart gdm service 

if no luck check display driver package for your H/W

---

### Post by Eric B on 2009-04-30
Thank you for your suggestion. I soon found that the install had several different issues. I just waited for Jaunty and upgraded, which went pretty smoothly.

---

