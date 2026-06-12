---
title: "dell 2208wfp not supported on dell reinstall dvd"
date: 2009-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ubunovice on 2009-06-16
I tried to install ubuntu 9.04 using the interactive installation option after booting from a dell 9.04 reinstall dvd. After some time my dell 2208wfp monitor says to me:
Out of range signal, cannot display this videomode, change computer display input to 1680X1050@60Hz ......... 
and the system hangs , power down is the only solution. 
I had the same problem booting from the Ubuntu 9.04.2 cd so after I heard about the dell-dvd I decided to try it .
Any help would be appreciated

---

### Post by coffeeaddict22 on 2009-06-19
Unusual default screen size.  
Boot the system up, go into a recovery console, and choose "repair my graphics system".  That may fix the problem.
If you plug in a different monitor, will it use that OK?

---

### Post by ubunovice on 2009-06-25
Hello Coffee
Sorry for my late reply but we've been out for a couple of days, 
I tried my wife's Dell 17 inch but then I do not even get a readable screen
Using the Ubuntu 9.04.2 cd  I then installed in 'safe graphics mode' and now I am running 9.04 using a 800*600 screen. The 'safe graphics mode' option was quite a hassle because
the installation-panels did not fit on my screen, but now at least I have a running system,
My next job will be to get a 'modeline' for my Dell2208WFP
Thanks for your help

---

### Post by coffeeaddict22 on 2009-06-25
Is this the intel graphics card problem?  What's the output of ```
lshw -C display
```

---

