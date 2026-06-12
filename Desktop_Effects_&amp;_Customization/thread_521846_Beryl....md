---
title: "Beryl..."
date: 2007-08-09
forum: Desktop Effects &amp; Customization
---

### Post by jeremy1138 on 2007-08-09
I have an HP laptop model number dv5020us and I've finally managed to get my video card to work...  I recently installed Beryl on this computer and for some reason I cant get it to do anything.  The little red diamond is up next to the date and time and all that and I can click on that and mess with settings and such but it wont let me choose Beryl as my window manager...  It always goes back to metacity.  I can choose the standard beryl decorator as my window decorator but that's it.  I can see a whole bunch of themes and such but I can't get any of them to load.  Does anyone have any idea what the deal is with this?  I am using Ubuntu 7.04 on an HP laptop with the amd turion 64 bit processor with 1024 MB RAM.  The computer has an ATI Radeon Xpress 200M video card and I widescreen display.  Thanks in advance for any help!

---

### Post by hedgefighter on 2007-08-10
When a program isn't working, it's helpful to launch it from a terminal. It'll spit any error messages out the terminal. Then chances are you can google the error message and find the answer. So, right click on the gem and choose Quit. Then open a terminal and start beryl manager:```
beryl-manager
```
Then again select window manager -> Beryl and see what is spit into the terminal.

---

### Post by jeremy1138 on 2007-08-10
ok...  Here's what it says: 
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
***********************************************

Any ideas?

---

### Post by Steveway on 2007-08-10
If you use the closed-source drivers provided by ATI, then you have to setup XGL.
Use the search for a Howto.

---

### Post by jeremy1138 on 2007-08-10
ok I found a how-to and I followed the directions exactly until it came to the part where I had to log out and then log in with the xgl gnome...  When I did that the screen looked all garbled and I couldn't read anything...  What do I do about that?  I followed the directions here --> [http://ubuntuforums.org/showthread.php?t=488385&highlight=xgl+how+to](http://ubuntuforums.org/showthread.php?t=488385&highlight=xgl+how+to)

Thanks for your help!

---

