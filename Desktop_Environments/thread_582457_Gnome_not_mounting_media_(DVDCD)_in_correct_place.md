---
title: "Gnome not mounting media (DVD/CD) in correct place"
date: 2007-10-19
forum: Desktop Environments
---

### Post by rxbandit on 2007-10-19
Running 7.04 w/ Gnome. I have two drives 1) CDRW/DVD 2) CDRW/DVDRW. Gnome automounts DVDs and CDs ok but it just sticks them under '/media'.

mythtv@mythtv-frontend:/media$ ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sda4  /dev/sdb1  /dev/sdc
/dev/sda1  /dev/sda3  /dev/sdb   /dev/sdb2  /dev/sdd

mythtv@mythtv-frontend:/media$ ls /dev/sc*
/dev/scd0  /dev/scd1

mythtv@mythtv-frontend:/media$ ls
cdrom  cdrom0  dvd  KNOCKED_UP

see my dvd "Knocked Up" gets mounted under '/media' instead of '/media/dvd'
I want to be able to stick a dvd in one of my drives and Xine or Mythtv be able to find it. Is it possible for this to work with either drive. Or am I just going to have to pick one drive to be a DVD drive? Cause say if i had two DVDs in. They both can't be mounted under '/media/dvd/'. So am I correct in assuming that for Xine or Mythtv to find a DVD, i can only use one of my drives to watch with. Since i don't think i can point it to look in more than one place :confused:

---

### Post by rxbandit on 2007-10-24
I still haven't been able to come up with a solution for this problem I am having. Hopefully someone out there knows what to do. :guitar:

---

