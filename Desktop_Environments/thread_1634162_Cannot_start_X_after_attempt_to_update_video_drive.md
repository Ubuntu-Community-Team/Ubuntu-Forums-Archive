---
title: "Cannot start X after attempt to update video driver"
date: 2010-11-30
forum: Desktop Environments
---

### Post by XEtedBear on 2010-11-30
While attempting to identify the cause of a crash in X, invoked by KMyMoney, following a change of graphics card hardware, I was advised to try another graphics driver. As a result my system start only in comand prompt mode and I cannot Startx.

Somehat foolishly I followed the Howto on installing the 'latest and greatest nVidia drivers'. The installation failed (most alarmingly because the driver that the nViida web-site identified as being appropriate  - X86-256.44 - actually issued an warning message during installation telling me that it did not support my installed hardware!). The recovery recommended in the Howto also failed (as I suspected it might).

If I press Ctrl+Alt+F7 at the command prompt I get many error/warning messages, starting with multiple instances of the following pair:

"unknown parameter encountered"
"ignoring unknown pararmeter"

and the system then enters a wait after the message 'checking battery status' - which confuses me, as, aside from the CMOS battery, there is no battery on my desktop system.

If I issue the startx command I get many error/warning messages
including:

"using config file /etc/X11/xorg.conf"
"using config file /usr/share/X11/xorg.conf.d"
........
"No devices detected"
"Fatal server error"
"No screens found"
......
"Giving up"
"xinit: no such file or directory (errno2): unable to connect to X server"
"xinit: no such process (errno3): Server Error"


What steps do I need to take to recover?

I am using Ubuntu 10.10, with an nVidia Quadro NVS 280 card and dual screens. This was a change from using a Matrox P650 for which I was unable to get any support for dual head operation. After the change I began by using the 'recommended driver' - nVidia version 173 - as recommended in <System><Administration><Additional Drivers>. That combination worked fine until my first use of KMyMoney, which resulted in an immediate (and I mean imediate - less than the blink of an eye) crash and burn of the X system.

---

### Post by XEtedBear on 2010-11-30
Should I assume then that it is not possible to recover a user-supportive, GUI-based Ubuntu from this state? That a full re-installation of the operating system is required - or I live with a Command line version only?

Really? In that case I'd be better off with DOS, wouldn't I? (much simpler, but less powerful commands, with far fewer options with easier to use documentation, which I already have in  printed form).

---

### Post by XEtedBear on 2010-12-30
Issue solved using the dumbest possible method: re-installed the op. sys. 

(The remote control for my car central locking system just failed; I think I'll take the car to be crushed....)

---

