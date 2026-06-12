---
title: "cannot switch users, login window problem"
date: 2006-12-08
forum: Desktop Environments
---

### Post by jules98 on 2006-12-08
Hello all,

I'm using Ubuntu 6.10 with ATI driver. Since about a week, I'm not able anymore to switch users:
I get a black screen with the rotating clock and nothing goes further. If I restart th X server with Ctrl->Alt->Backspace, I got a popup window asking for the password of the current user...

Can anyone give me some hints where to look for (log files? config files?) or help to troubleshoot....

Another symptom of the problem:
When I'm booting, I see the following:
- The BIOS screen
- The GRUB screen
- The Ubuntu splash screen
- A black screen (the graphic card switch swtiches the video mode?)
- The rotating clock
- A popup saying "The greeter application seems to be failing, trying another one" with an Ok/Cancel button.
- When I click the Ok button, I get a login window WHICH IS NOT the one I have choosen in the "Login window" manager...

BR, Jacques-D.

PS: I have just install Ubuntu on an other partition with same CD and I don't get the problem, so it's most probably not related to the hardware...

---

### Post by studiesrule on 2006-12-08
If its working on another partition, why don't you just get rid of this one? 

If thats not an option, press Ctrl+Alt+F2 at login to enter the text login. Login, and type:

sudo dpkg-reconfigure xserver-xorg.
This should reconfigure your Xorg config files. if its an X problem, then this will fix it (i'd say with a 90% probability). Try it several times, with different options like use the standard vega drivers or the opensource ati ones. If that doesn't work, then look in /etc/X11/xorg.log (i'm not 100% sure on this one) for the log file

---

### Post by jules98 on 2006-12-08
I have try the reconfigure Xorg, using all default settings: same problem!

The log file you mean is probably /var/log/Xorg.0.log

At least something is interesting here: there is 2 files:
Xorg.0.log, dated "Fri Dec  8 18:04:07 2006"
Xorg.0.log.old, dated "Fri Dec  8 18:04:01 2006"

I don't see any major differences between these out of some memory adresses.

If you need, I can post a copy of them.

Any other suggestion?

For me, the problem is not in X, but in gnome: I suspect wrong rights somewhere.

Do you now how the login window starts? I mean as which user?

---

