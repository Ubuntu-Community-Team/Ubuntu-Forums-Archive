---
title: "Xubuntu 14.04 boot process stops at &quot;stopping log initial device creation.&quot;"
date: 2014-06-13
forum: Desktop Environments
---

### Post by hr_trivedi on 2014-06-13
Hello. I'm running Xubuntu 14.04 fully updated as of writing this post. There are no held or broken packages. My problem is since yesterday Xubuntu boot process stalls at,
```

Hr-desktop Login * stopping cold plug devices. [ok]
* stopping log initial device creation. [ok]

```
I boot Xubuntu, The plymouth screen appears, Then it goes away and there is nothing but a black screen, I press 'Esc' key but still nothing. If I press 'Ctrl+Alt+F1' here then the above two messages appear on the screen and it remains stalled here. If I press 'Ctrl+Alt+F2' then the tty2 login prompt is there. I can login here and running 'startx' makes the XFCE desktop appear. I also tried running,
```
sudo service lightdm start
```
from the tty2 and the response was,
```
Start Job is already running : lightdm
```
Any help is greatly appreciated.

---

### Post by Bucky Ball on 2014-06-13
Welcome. Was the machine running fine prior to the update? Do you get a list of kernels to choose from when you boot from the computer? If you do I suggest you choose the previous kernel and see if you have the same problem.

If you don't get that list to choose from at boot, hold down shift after the BIOS screen and that should get you to the list. Then choose a previous kernel. Not a fix, but at least we can get into to a stable install to tweak. If it doesn't work, it gives us the info that the problem is not restricted to that one kernel, but something global.

---

### Post by hr_trivedi on 2014-06-13
Thanks for a prompt reply Bucky Bell.
I have two kernels. I've tried booting with the previous kernel and the problem has persisted. So for sure this is not a kernel problem.

---

### Post by syntaxerror74 on 2015-02-22
Apologies for exhuming this 1-year-old thread, but I've run into the same problem with **L**ubuntu, not Xubuntu.

However, I can give a more verbose explanation HOW I got my system to hang at this point...

Due too many clickety-click sounds that reached my ear from inside my PC, I thought that now it is time to CLONE the whole system to a near-identical HDD and no longer use this one for the main system (WAY too much of a risk).
Fired up Boot-Repair CD (what a inestimably great piece of work!), copied partitions with GParted exactly as they were in the old system ... except for resizing here and there. (As a matter of fact, I had left some 50 GiB of unused space at the end last year on the source HDD to have some "room to maneuver" when cloning: a wise thought!)

Installed GRUB on MBR.

Like the OP, I too have two kernels at my disposal. Tried 'em both - no luck.
```
Stopping log initial device creation
```
Pressing **ESC** to reveal what is going on, this is the very last I get from my system, except for ever-circulating dots at the graphical "login" screen. But no login.

Does anyone have an idea how this can happen "just" by cloning the whole system??


---------------------------------------------------------------------------------------------------
**SUCCESS! HOORAY!**

Got it solved in my case.
The reason was (as usual) most bewildering...

**/var** was moved to its separate partition in the new installation for sensible reasons (this sonofab*tch can get quite big, and I didn't like the thought that it would always bite down its storage space off the **/** partition)
However, I would not have touched this (yet) if I had known how STUBBORN some Linux software can be!
While I used some effort to track things down, I learned that **lightdm** indeed has the nerve to FAIL if **/var/log/lightdm** does not _exist_!!!

(Dammit, it's only a LOG file! Heck, if you can't write it anywhere, just try to get over it! And have you ever thought about *creating* the directory if it's not there? This would have left me with a pseudo-/var which I would have moved to /var_old after the next /etc/fstab update to be on the safe shore. But no...)

Anyways, I'm back in my good ol' distro. Feels nice.
And to any Windows guys reading this: THIS is the difference between you guys and us. We won't reinstall our whole OS if something fails, for we are courageous enough to track down the problem and fix it. :P:biggrin:

---

### Post by astraluxkl on 2015-06-02
In my case when I got same error I just presed esc an presed CTRL+C to skip freezed processes
------
Ubuntu Desktop 14.04.2 LTS

---

### Post by Bucky Ball on 2015-06-02
Old thread now closed.

Please post a new one outlining your issue and with a descriptive title if you still need support. Good luck.

---

