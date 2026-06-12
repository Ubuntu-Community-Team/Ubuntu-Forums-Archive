---
title: "Mathematica under Ubuntu"
date: 2005-12-10
forum: Desktop Environments
---

### Post by kpturvey on 2005-12-10
I just installed the trial version of Mathematica under Ubuntu on my laptop.  It uses Motif so I assume this is probably a problem with the lesstif libraries (that's what Ubuntu uses isn't it?).  Anyway, Mathematica runs fine, but after running it my panel doesn't work correctly it loses the alternate desktops and in general doesn't function like it is supposed to.  I tried killing it using xkill and also killing X altogether and restarting it.  Neither of these solutions fix the problem.  It seems that the only solution is to reset the computer.  This feels a lot like running Windows.  

Is there a fix for this problem?

Thanks in advance.

---

### Post by kpturvey on 2005-12-17
Another thread recomended using prelink.  That didn't solve the problem for me and didn't provide any noticable improvment in performance.  

I did figure out that rather than rebooting I can just kill wnck-applet (it runs using 100% of cpu after starting Mathematica) and hit reload on all the dialog boxes that pop up and I'm back to a usable system.

It is still annoying, but not a show stopper.

---

### Post by kpturvey on 2006-02-11
I finally got a complete fix for this problem.  Prelink isn't it, but it is quite simple.  Just start Mathematica with the option "noSplashScreen"

like so:

$ mathematica -noSplashScreen

I honestly don't know why, but this prevents the program, wnck-applet from spinning out of control.  

:D

---

### Post by taurus on 2006-02-11
You can always install OpenMotif (free version of Motif) if you don't want to use lesstif!!!

[http://www.openmotif.org/](http://www.openmotif.org/)

---

### Post by astronerd on 2006-02-12
I use mathreader(from the wolfram site) to read mathematica notebooks and I get the same CPU problem that takes up 100%. It is a pretty crappy deal, cause anytime I open a notebook it causes this problem.  Is this fix going to help me out, or does it only work when you open the actual mathematica software/program?

---

