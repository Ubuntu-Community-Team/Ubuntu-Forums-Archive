---
title: "Shutdown/halt/poweroff reboot the laptop - intrepid"
date: 2008-11-03
forum: Desktop Environments
---

### Post by firestorm10 on 2008-11-03
Hi,
the title pretty much sums it up.  No form of shutdown other then holding down the power button seem to work.  I tried the normal shutdown, then I tried with the terminal using all of these:

[INDENT]shutdown -h now
halt -p
poweroff[/INDENT]

I have no clue what to do and all the answers I have found are for previous versions of ubuntu and Intrepid doesn't have the folders/modules they point to.  Also I don't know if this has anything to do with it but sometimes boot up freezes when loading powernowd.

Thanks to all that can shed any light to this matter.

 -David

PS: I'm kinda newbish linux wise.

---

### Post by firestorm10 on 2008-11-05
Bump

Anyone care to help?

I know it's not something evil, just freakishly annoying.

---

### Post by techflat on 2009-02-25
Hi there, maybe you solved this problem, but maybe I can help or at leat give you a light on how to start to solve this...

I guess the problem could be:
[LIST=1]
[*]The system installed has a problem and it reboots because of this.
[*]You (or someone else without you knowing) have configured your computer in the BIOS in a way it reboots every time.
[/LIST]

To check nº1 you should look at the next command, it's a log of the system boot up. Maybe you can see if there's a problem there.
```
dmesg | less
```
I don't know but I'm guessing there's also a log for the shut down.

To check nº2, enter the BIOS setup and find out what does every configuration parameter and check if they're on the correct state.


Hope this helps, even if it's too late...
Cheers

---

