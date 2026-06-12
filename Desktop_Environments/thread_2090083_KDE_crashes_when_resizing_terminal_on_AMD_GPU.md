---
title: "KDE crashes when resizing terminal on AMD GPU"
date: 2012-12-01
forum: Desktop Environments
---

### Post by ibbles on 2012-12-01
Hi

I'm using Kubuntu 12.10 and having problems with the terminal. Sometimes when  I resize a window with a terminal in it (tried Konsole, xterm, and terminator) I get kicked out of KDE and has to log in again. All running applications are of course killed as well.

I've seen quite a few other threads about this particular problem, but the consensus appears to be that NVIDIA drivers are to blame and I  have a AMD GPU.

Anyone else with a AMD GPU experiencing the same problems? What can I do to fix it?

System:
Kubuntu 12.10
AMD 5800k APU (AMD Radeon HD 7660D)
MSI FM2-A85XA-G65

ccc says:
Driver Packaging Version 9.00.11-120920a-147436C-ATI
2D Driver Version 9.0.2
Catalyst™ Control Center Version 2.17
RandR Version 1.3

---

### Post by ibbles on 2012-12-03
Perhaps related, I have a setup with three monitors and if I turn off the one in the middle and then turn it on again, then the other two monitors flash for a second (like if going into sleep mode and then immediately woken again) and then I'm kicked back to the login screen again. The monitor in question is connected via DisplayPort.

---

### Post by Nintendon't on 2013-01-06
I also have this problem, it happens to me frequently, causing me to lose all work since the last save. It's incredibly frustrating.

---

### Post by lprent on 2013-04-19
I'll leave this for searchers.

It is definitely on the radeon drivers. This shows up when I use the current drivers from AMD. It goes away when I'm on the open source ones. 

I'm currently on the development kubuntu 13.04 using 13.3 drivers from AMD. I have previously seen this on 12.10 with earlier drivers.

The behavior has now shown up on two different radeon's. A 7750 and what I think is a 6450 (I had to drop down a grade when I needed a new slot for USB 3) where in each case I have started from no drivers, gone to open source , then eventually back to the open source drivers (which I'm just about to do now).

Updated: [http://www.omgubuntu.co.uk/2011/10/five-alternative-terminal-emulator-apps-for-ubuntu](http://www.omgubuntu.co.uk/2011/10/five-alternative-terminal-emulator-apps-for-ubuntu)
Terminator does the konsole replacement job quite nicely without crashing like all of the standard consoles are doing. I left Yakuake running  as well for those quick commands like looking at logs. The others didn't look industrial strength.

Looking through the bug reports, this appears to be a regression problem down in the recent Xorg 1.13 used in ubuntu 12.10 and 13.04. It may take some time to get resolved.

---

