---
title: "Xinerama triple head issue"
date: 2009-02-13
forum: Desktop Environments
---

### Post by badlee on 2009-02-13
hi, i have a Kubuntu 8.10 system with two nvidia 9600 graphics cards. I am having issues with the x-server freezing, it does it randomly where the mouse still works, but cannot click on anything. Then there is the general lag time between moving the mouse that happens every now and then. along with the plasma application not responding and causing the system to be unresponsive for a period of time and perhaps making the x-server unusable. And lastly, the video playback from any video source lags when multi-tasking, i am not running any cpu intensive tasks, just a video and checking my e-mail. 

Does anyone have a clue what the problem is and how to resolve it? 
it also tells me i am missing the RANDR extension when i start some programs 

my thought is that it is xinerama due to what little info i found online, but are there alternatives to it? 

here is my x-org file and the log file.

---

### Post by badlee on 2009-02-17
After receiving an upgrade to the kde environment, most of the bugs had been worked out. The graphics are seldom still sluggish or slightly messed up(pixilated and non-responsive to changes on the screen, but the programs are still just fine) but requires a restart. 

The last thing is that i still cannot play any games. the mouse freezes anytime a game starts, but the programs are still good to use with the keyboard, and everything is normal but the mouse.

any suggestions?

---

### Post by ghstridr on 2009-02-23
I've got the same problem except under Gnome.

---

### Post by ChiaGod on 2009-04-27
For anybody still having this issue or coming across this by searching, I believe it is related to this issue which is fixed in Jaunty:

[https://bugs.launchpad.net/ubuntu/+bug/296167](https://bugs.launchpad.net/ubuntu/+bug/296167)

---

