---
title: "What is the lightest window manager?"
date: 2009-04-05
forum: General Help
---

### Post by willz06jw on 2009-04-05
Hi and thanks for the help,

I am running command line only ubuntu.  I use fluxbox to launch programs that need a windows manager.  What is the lightest windows manager available?  My computer is a piece.

Thanks!
Will

---

### Post by mb_webguy on 2009-04-05
[TinyWM]("apt:tinywm") is probably the lightest at only 102KB.  [JWM]("apt:jwm") is only slightly heavier at 324KB.  I personally prefer [Openbox]("apt:openbox"), which at about 1500KB (plus dependencies) is still less than half the size of Fluxbox.

---

### Post by .Maleficus. on 2009-04-05
Try out Dwm.  On my machine right now it's using about 21MB of memory (if I'm reading pmap right).


Edit:  Seems as though that's the memory usage with all of the extra things that Dwm is calling (ie, X and such).  The actual Dwm process is 1.4MB (if I'm reading the output of 'ps -AH v' right ;)).

---

### Post by willz06jw on 2009-04-05
Great ideas -- I will check them all out.  

As I mentioned earlier, my computer is over a decade old and doesn't have the gusto it used to have back in 97.  The video flickers even with TinyWM.  Is this being caused by something else?

Thanks,
Will

---

### Post by kerry_s on 2009-04-06
i use jwm on 450mhz 256mb ram, it's a 10 year old laptop.

---

### Post by willz06jw on 2009-04-06
That looks great!  I am afraid your computer outpowers my celeron though.  Does your screen flicker when you move/resize windows?

Thanks,
Will

---

### Post by 3Miro on 2009-04-06
I used to play with windows maker. If your machine is that old, consider a distro that is designed for old computers (there were couple such things), or try to find an old version of Linux.

---

### Post by willz06jw on 2009-04-06
It even flickers on DSL and Puppy. Do you think it could be another type of problem?  I don't think even an old celeron should flicker with lwm or tinywm.

---

### Post by kerry_s on 2009-04-06
> **willz06jw said:**
> That looks great!  I am afraid your computer outpowers my celeron though.  Does your screen flicker when you move/resize windows?

Thanks,
Will

no, no flicker its just fast. :D

what is your specs, the more you tell us the better we can inform you.

> It even flickers on DSL and Puppy. Do you think it could be another type of problem? I don't think even an old celeron should flicker with lwm or tinywm.


flickering would be a vid issue, say like wrong drivers or could be your screen is just crap. really old screens had flickering, can you tell us about your screen.

---

### Post by Anzan on 2009-04-06
Try Xmonad.

---

### Post by willz06jw on 2009-04-09
It's a new (in a relative sense) LCD monitor.  The celeron is a 333Mhz with 64MB of RAM.  I don't know what type of video card it has -- but I am sure it is generic.  I will check and post when I get [my wife gives me] a second.

Thanks again for all of the suggestions, reads, and help.

Will

---

### Post by kerry_s on 2009-04-09
ouch, with something that old your bound to see slow drawing, but flicker?
look at your /var/log/Xorg.0.log

---

### Post by soltanis on 2009-04-09
This just in: DWM is possibly the tiniest window manager ever.

But my personal preference for ultralight WM? TWM. I'm not even sure this is even distributed anymore, but try it (its fun!)

---

### Post by willz06jw on 2009-04-12
VGA compatible controller: S3 Inc. ViRGE/DX or /GX (rev 01) -- This is my video card.



Thanks,
Will

---

### Post by willz06jw on 2009-04-13
Everything on the log file looks OK  (IE no errors 
and such).  Also let me mention that it only fickers 
when resizing/moving/doing anything.  It doesn't 
flicker at all when just looking at dillo without 
scrolling.  Sounds like a not-enough-horsepower 
problem.

Thanks for the help anyway,
Will

---

### Post by 3Miro on 2009-04-13
"Lightest" windows manager depends on the apps that you wish to run. For example, if you install gnome, but run only KDE apps, gnome would be much heavier. Likewise, if under KDE one uses FireFox, KDE becomes heavier than if you use Konqueror.

The reason is the amount of extra libraries that you need to load. Not much of an issue if you have a lot of RAM (only slower initial startup), but may be a drag on a weaker system.

You may run the "lightest" desktop out there, but loading a non-native browser (say FF) would make you load a bunch of extra libraries and the thing will slow down immediately. FF needs some GTK libraries to run. Suppose that in addition you load KDE's Amarok, then you will need to load QT4 libraries and then the entire thing becomes heavier than just running Gnome with gnome native apps (well something along those lines).

Pick something that is simultaneously lighter and has enough "native" apps so you don't have to load too many extra libraries.

---

### Post by willz06jw on 2009-04-15
Well my computer is a little behind that logic (I think).  I can't run GDM or KDE since the computer only has 333Mhz and 64MB of RAM.  I am using LWM and it is pretty basic (no taskbar and only manages windows by moving your mouse over different windows)....but I bet this thing would fly with a Pentium 3!  I am using the alternative command-line-only install.

Thanks for the help though,
Will

---

