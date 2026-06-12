---
title: "cant run software packages i download with synapse"
date: 2005-11-26
forum: Desktop Environments
---

### Post by recklessray on 2005-11-26
hi, certain packages i install in breezey dont run - here is what it says in terminal when i try to run ppracer; this is a good example as it always refers to the same problem: Xlib:  extension "GLX" missing on display ":0.0". and segmentation fault ???

any help most apreciated ;)

ray

ray@ubuntu-box:~$ ppracer
PPRacer 0.3.1 --  [http://racer.planetpenguin.de](http://racer.planetpenguin.de)
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Success)
Segmentation fault
ray@ubuntu-box:~$

---

### Post by GeneralZod on 2005-11-26
That means you don't have 3D enabled for your graphics card.  What kind of card do you have? Hopefully not an ATI! ;)

---

### Post by recklessray on 2005-11-26
hi there, thanks for the reply. 

my graphics card is an nvidia geforce with 128mb ram.

cheers

---

### Post by GeneralZod on 2005-11-26
Have you tried installing nvidia-glx and restarting X? I don't know how up-tp-date this guide is, nut you might want to try it out:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by bb002 on 2005-11-26
[edit]

....seems only the first post loaded and i replied like there hadn't been any replies. oops.

---

