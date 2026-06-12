---
title: "xserver isnt starting..."
date: 2005-10-28
forum: Desktop Environments
---

### Post by redneckr1 on 2005-10-28
help i apt-updated last night, and it updated a load of packages (was running through the breezy multimedia guide because i want to play wma's) and i restarted and xserver didnt start and i plainly dont know what to do in a command line ubuntu setup.

it says i need to configure xserver? how do i do this as i need to also start a project pretty soon. also the other vexing thing it said ubuntu doesnt come with any warranty. what a time to reiterate it lol 

please help

---

### Post by psychicdragon on 2005-10-28
Try this: **sudo dpkg-reconfigure xserver-xorg**

---

### Post by redneckr1 on 2005-10-28
will try and report back as im in a uni lab atm :)

---

### Post by redneckr1 on 2005-10-28
well i managed to get gnome to run using your advice and following the package information i now have this problem tho

its

>  xsession warning xrdb command not found. xresources not merged 

i have an image of the offending thing [here](http://server2.uploadit.org/files/kingred7-Screenshot.jpg)


help me i am bloody stuck now, i have tried reinstalling the fonts and xserver. im out of ideas now

---

### Post by psychicdragon on 2005-10-28
That's pretty strange. Is it just Firefox that looks like that? The panel looks fine...

I'm not really sure what xrdb is, the man page didn't help me out much.

Make sure it's installed I guess.```
sudo apt-get install xrdb
```If that doesn't work, can you post your **/etc/X11/xorg.conf** and **/var/log/Xorg.0.log** here?

---

