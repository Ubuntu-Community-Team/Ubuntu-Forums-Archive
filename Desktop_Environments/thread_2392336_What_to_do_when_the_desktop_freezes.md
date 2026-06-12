---
title: "What to do when the desktop freezes?"
date: 2018-05-19
forum: Desktop Environments
---

### Post by pythagorean1804 on 2018-05-19
I am running Ubuntu 18.04 (the official one, with the gnome desktop).  I also use the NVIDIA driver metapackage nividia-driver-390 (proprietary, tested) because I use the Hiri email client and it complains about the xserver-xorg-video-nouveau driver (saying with an alert that the nouveau driver is known to cause problems).  I have a GeForce GT 740 graphics card.  It's a desktop computer with 32 GB of ram and a xeon processor.  I used to run Windows 10 on it and that always worked perfectly fine.

So, every once in a while here in the last week (like... several times) the desktop completely freezes up.  I can move the mouse around but nothing is clickable and nothing accepts any keyboard input.  I can't type anything anywhere.  I can't click anything.  All I can do is hold down the power button to turn it off and then restart.

I would like to know if anyone has a suggestion for how to recover from such a disaster without having to power off the computer.  That seems like a catastrophe waiting to happen.  I would like a suggestion along the lines of CTRL-ALT Delete to get to a point where I could kill a process or something.

Suggestions?

---

### Post by vanadium on 2018-05-20
Some possibilities:
1. You may need to enable the possibility of killing X with Ctrl+Alt+Delete: [https://askubuntu.com/questions/839836/enabling-ctrlaltdel-for-x](https://askubuntu.com/questions/839836/enabling-ctrlaltdel-for-x). Once you enable this, that key combination should kill the x server and bring you back to a graphical login screen
2. If possible, switch to a virtual console with the key combination Alt+Ctrl+F3 (or F4, F5, or in Ubuntu older than 17.10 F2, F2). Login on the text screen and restart the system with the command "sudo shutdown -r". Actually, from that command prompt, if you can get there it should also be possible to restart the xserver with a command, but I am not aware how.
3. Last resort: Keep Alt+PrtScr pressed (notably on laptops, might need also to use the Fn key). Then slowly and in sequence press the keys r e i s u b. This reisub key combination gives commands to the kernel to release the keyboard, unmount file systems etc, and finally (the b) to reboot the system, and would be a drastic though safe way of rebooting a system that is not responding.

---

### Post by pythagorean1804 on 2018-05-20
@vanadium I appreciate your help!  I added 

> XKBOPTIONS="terminate:ctrl_alt_bksp"

to my /etc/default/keyboard with

> sudo -H gedit /etc/default/keyboard

and yes I find that it does return me to the login screen.  Unfortunately upon logging in everything that was open before is now closed, so not much of an improvement over simply rebooting via the power off button.  I tried Alt+Ctl+F3 and nothing happened.  So I did the same with F4 and F5 and still nothing.  So suggestion 2 didn't change the outcome.  Option 3 is, for me anyway, the same as just rebooting with the power off button.

So I am sticking to option 1.  It does at least result in a change in the system that allows me to resume working sooner rather than later.  I save my work often enough that it won't be a huge catastrophe if the system keeps freezing.

Over time as I research this issue I hope to find some way of resuming the system with the files and processes I had running restarting in their last good state without having to restart every program from scratch and losing all of my open work when the system failed.

Thanks again for taking the time to spell out each suggestion.

---

### Post by vanadium on 2018-05-23
> **pythagorean1804 said:**
> Unfortunately upon logging in everything that was open before is now closed, so not much of an improvement over simply rebooting via the power off button.

You did ask how to avoid a hard shut down. This is what I answered to. I know that all my suggestions also lead to losing your current work, but they allow to rescue the system more gracefully and in a safer way than with a hard reset. Of course, something is causing the freezes on your system, likely some driver issue, so the better solution would be to have these solved.
> 
  Option 3 is, for me anyway, the same as just rebooting with the power off button.

Not sure if, technically, it is the same. Option 3 might be safer than the power off button. With a hard reset, you always run some risk to break your file system.

Probably a driver, or even a specific hardware issue on your system, might be the culprit. If the latter, your system will break down on it anytime sooner or later (I once had such experience with a hard drive). If the former, then hopefully a future update will bring a solution.

---

### Post by Holger_Gehrke on 2018-05-23
Option 3 is a lot safer than just cutting the power. Each keypress triggers an action. 'S' does a sync, so everything in cache that needs to be written will be. 'U' unmounts all file systems. 'B' does the reboot. Obviously you should leave enough time between the keypresses for the respective action to complete.
And you really should look into getting the virtual consoles to work. They are **very** helpful in diagnosing the source of the problem and possibly fixing it. Anecdotal evidence: I sometimes have a similar problem when playing quake using darkplaces in fullscreen. If I forget to disable xscreensaver and take a break, the screen saver will come up and after that quake won't react to any input (but it is still running, it continues to make noises). Going to a virtual console, killing darkplaces and switching back to the GUI gets me back to a working desktop.

Holger

---

