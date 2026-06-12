---
title: "Desktop Freezes During Drag and Drop"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by jimmybondo on 2007-10-26
So here is the problem, whenever a drag and drop is initiated with the KDE desktop environment, the entire desktop freezes. I have a hunch that this is due to compiz as it does not freeze when kwin is used instead.

Steps to recreate (at least on my machine):
start kde, compiz
start kopete, login
try to drag a name to another folder

At this point, the screen freezes and the computer becomes (almost) unresponsive. Music will still play in the background, hardware volume control works, and the mouse still works. These are probably controlled outside the window manager so they should not be affected. I cannot switch into another terminal session (Cntrl+Alt+F1), so it is tough to recover from the error. Perhaps a system call is not implemented or an error occurs, but I receive no feedback.

Here is my machine specs:
Thinkpad T43
1.7Ghz
Intel Integrated graphics
Kubuntu Gutsy 7.10
All compiz updated out of the current repository.

I could not find any logs that might be necessary, but if any are required, please let me know.
Thanks,
Jim

---

### Post by allstar1971 on 2007-11-05
I am having an issue that is SOMEWHAT related.

My computer will lock up if too many windows are open or if my screen saver is on while I am away. 

When I ran Feisty, my computer would run all night and no problems. Now, I come back and everything is frozen. I need this solved ASAP! I do not want to keep rebooting all the time.

Sometimes I will be working on my computer and have music playing in the background and then the computer freezes up and my music keeps sounding like an old record that is stuck in a groove. (It repeats the same  couple words over and over.)


JP
AMD 3700+ 64-bit
Nvidia GF4
1GB memory

---

### Post by sahilbhrany on 2007-12-03
I had the same drag n drop freezing problem as well, but i am using Ubuntu 7.10. haven't tested it without compiz running though yet. i have also noted if i click rapidly the system freezes as well. same problem music video playback continues, only the mouse moves, keyboard is unresponsive.I am using a lenovo n100. Does anyone have any idea about this problem?

seems there is problem with the reflection plugin in compiz, you need to disable that for drag and drop to work properly, its been working fine so far for me now.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/147018](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/147018)

---

### Post by sirab on 2008-01-04
Thanks! Disabling reflection worked for me.

---

