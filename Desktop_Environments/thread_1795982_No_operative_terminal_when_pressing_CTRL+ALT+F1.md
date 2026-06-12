---
title: "No operative terminal when pressing CTRL+ALT+F1"
date: 2011-07-03
forum: Desktop Environments
---

### Post by Pablo33 on 2011-07-03
Can't get into terminal mode by pressing any hotkey CRTL+ALT+F1 .... F6  

Displays seems to freeze, a blank screen is shown whit some bright spread pixels at the top. Although I can return to graphical mode by pressing CTRL+ALT+F7 without problems.

What can I do? 

System data:
**Ubuntu 10.04 (lucid)**
**Gnome: 2.30.2 (Ubuntu 2010-06-25)**
**X.Org X Server 1.7.6**
**kernel** **2.6.32-32-generic **
video card: 
**GeForce 8600 GT, PCI-E 16x, 512Mb**
NVIDIA driver version: 173.14.22

---

### Post by Pablo33 on 2011-08-17
Well, I've noticed that also freezes when logging an user out, or changing from one user to another.  I really don't know where the problem is. :confused:

I'm getting used to restart the machine every time I have to change user or to kill an unstable process. Luckily it doesn't happen very often. Love Ubuntu! :razz:

bye.

---

### Post by valantis on 2011-08-17
> **Pablo33 said:**
> Well, I've noticed that also freezes when logging an user out, or changing from one user to another.  I really don't know where the problem is. :confused:

I'm getting used to restart the machine every time I have to change user or to kill an unstable process. Luckily it doesn't happen very often. Love Ubuntu! :razz:

bye.

Hi on system management at keyboard the shortcut keys  that is defined.
make a update if you have to make and remember if you make intallation a program and this it's make it after. 
You can also look at startup programs if it run something that you don't realy use.

---

### Post by Pablo33 on 2011-08-18
The splash logo of "ubuntu" when starting or shutting down the computer has also gone.

I start thinking that it's a problem of x-org or the graphic card, because the symptoms are always the same. Something is wrong while system try switching from desktop resolution to "terminal resolution" or "log out resolution", even when trying to switch and show the "ubuntu splash" while starting or shutting down the computer.

I'll try to make a "blinded" log in in a terminal mode after pressing ctrl+alt+F1,  because it seems to be there although I only can see a black screen with some white lines and plots up there moving slightly. I'll post the results.

---

### Post by Pablo33 on 2011-08-18
Yes, I was right. Although I can't see nothing, the terminal is there and active, I could get logged in and type:
```
$sudo stop gdm
$sudo start gdm
```As a result I could restart my desktop environment starting from the user loggin screen. But, the new desktop shows different icons. Not gnome, but kde icons?? :confused:

I still think it's a video card failure, I don't have any idea.

By the way, recently I plugged a second screen to the computer, I'm working with separated screen configuration, and also independent desktops. System can't cope very well when trying switching video resolutions without restarting (on live mode). I think it could be issued by the same thing.

Video card failure?, video module doesn't work properly?.  who knows?.

Luckily it is a minor failure that I don't mind it very much.

thanks for your reply.

---

