---
title: "Problems booting up after installing"
date: 2009-01-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by radikaluser on 2009-01-04
Installation for 8.10 went fine, but after i rebooted and put in my user name and password in and pushed enter, the screen went black and all it has on the screen is the cursor.  I previously had Breezy and just wanted to update and this happened.  Thank you for the helping.

---

### Post by natehall on 2009-01-04
Try startx in a terminal. ( ctrl alt f1  should bring one up if you don't already have one.)

---

### Post by radikaluser on 2009-01-04
I had to reboot because it seemed as if it froze up.  When I did so it turned on for a minute and then the monitor when off line.  So I rebooted again and entered the system by pressing ESC and accessed the terminal that way.  I typed in startx and a screen came up that was a colorful patterned and froze again.  Any other advise?

---

### Post by natehall on 2009-01-05
Use a live cd to start the machine then back up any data on memory sticks. I've had so much problems with updates I just do fresh installs now.

---

### Post by radikaluser on 2009-01-05
I had backed up all of my stuff prior to the update to 8.10.  But the truth is, I can't even get the live cd to boot past that same point, right before the KDE boots the desktop.  I am obviously going to have to do something in the terminal, but were to I start.  I have already tested the integrity of the cd, and installed it for a second time.  When I first installed, I set the partition with my old kubuntu. When I booted and it did not work, I installed again and set the partition were it would erase my hard drive.  I just need some ideals of why it may not be working correctly.  Thanks for the help

---

### Post by Mr_Sandman on 2009-01-05
I have the same issue with Ubuntu 8.10...

installs fine, after logging in it locks up...

the system isnt "hung" or frozen, you can still press numlock on and off (but, for some reason, not caps or scroll locks?)...

i did a tiny bit of research and someone suggested the "alternate" distro... im going to try that out tomorrow, unless someone can confirm that it wont work by then...

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

(first two listed there, for those looking for the DL links)

---

### Post by andybleaden on 2009-01-06
Alternatively you can try booting the live cd and then try the safe graphics mode (press f4 and select safe graphics mode) just before selecting the try live cd option.

Let us know how you get on

---

### Post by Mr_Sandman on 2009-01-06
> **andybleaden said:**
> Alternatively you can try booting the live cd and then try the safe graphics mode (press f4 and select safe graphics mode) just before selecting the try live cd option.

Let us know how you get on

i tried this, it didnt work (for me, anyway)...

the monitor im using doenst support the resolution that its displaying...

---

### Post by radikaluser on 2009-01-06
It actually worked for me.  I called up a friend who knows about this stuff.  I will post later if I find anything out.  Thanks for the help

---

### Post by Mr_Sandman on 2009-01-06
UPDATE:

i decided to try installing an older version of ubuntu (7.10) and that worked fine... i updated to 8.04 and thats working...

im reluctant to update to 8.10...

---

### Post by radikaluser on 2009-01-07
I tried installing 7.10 but it wouldn't even boot the live cd. It will start as if it is going to, but then it just default to loading 8.10   I called my friend and he said it might have something to do with ownership/permissions, but i chown -R my username and the same problem.  No solution now but hopefully soon.

---

### Post by natehall on 2009-01-09
Are you sure its booting from the CD? You may have your BIOS set up so that it won't use the CD first or if you have an old enough computer the BIOS won't even have a CD boot option.

---

### Post by andybleaden on 2009-01-14
Perhaps that can be examined by rebooting and hitting F12 after the initial boot screen comes up. Here it will display your boot order.

Sounds more like graphics card issues to me. Have you run any ubuntu based package before successfully on this pc?

---

