---
title: "Dell Inspiron 1520 and Ubuntu issues... begging for help."
date: 2011-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rtierney on 2011-03-25
I've tried installing Ubuntu 10.04 and 10.10 onto my Dell Inspiron 1520, and something goes wrong.
I tried a couple ways...
First off, I tried installing Ubuntu within Windows, and it said the install went fine, and Windows see the Ubuntu app in software.
When I reboot, and select Ubuntu to boot into, it gives a an ugly purple screen, and won't go past it.

I also tried installing from a CD.
When loading, it shows the first screen before the Ubuntu installer with the little man at the bottom, and when it's done loading and would normally go into installer screens, the whole screen just goes purple instead.

For some reason it only does it with Ubuntu 10.04 and 10.10.
When I tried Ubuntu 9.04, it went through just fine with everything.

Can someone please shed some light on this issue, and possibly give me a solution.
I've been beating my head on this for quite some time now.
:/
And to be honest, I just really want Ubuntu up and running.

Ultimately, I don't want the whole disk to be Ubuntu, I want to be able to dual boot.
I'm begging for someones help! 
>.<

---

### Post by ajgreeny on 2011-03-25
When you get to the screen with the man and keyboard icons hti return then choose language and finally hit F6.  This allows you to use different kernel options to boot.  Try **nomodeset** and see if it helps, as I suspect that your problem may be a graphics card problem.

---

### Post by rtierney on 2011-03-25
Thank you for the reply!

I was thinking the same thing after a little while.

Let me try your suggestion and I will get back to you in a sec.

---

### Post by rtierney on 2011-03-25
Ok...
I selected nomodeset from F6, and then continued to Install Ubuntu.
It now won't load past the screen after that.
:/

---

### Post by rtierney on 2011-03-25
Tried a test, and running the installer normally in text mode works just fine.
So I'm taking it that this is a graphics card problem.

What would you suggest?
Strange that other versions work fine.

---

### Post by ajgreeny on 2011-03-25
You could try fully installing in text mode, then if necessary getting the graphic driver you need either with the command line or, if it will work for you, by trying failsafe gnome from the session menu of the login screen, then using the additional drivers menu item from System ->Administration.  I can not really help more with this as I have not had graphics problems and have always used the open source drivers for my old ati card.

Good luck.

---

