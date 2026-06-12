---
title: "Auto updated now X won't start"
date: 2007-02-11
forum: Desktop Environments
---

### Post by Tad2much on 2007-02-11
I'm running edgy eft and beryl on my desktop.  Before I went to bed last night I ran the auto updater which updated my kernel version so I just turned the computer off since I'd have to reboot anyway for the upgrade to take effect.  So this morning when I turned it on I am getting errors and my X-server won't start.  It says:

Failed to load module "wfb" (module does not exist, 0)
Error: API mismatch: The NVIDIA kernel module has the version 1.0-8776, but this X module has ther version 1.0-9746.

as well as some other stuff, but that seemed like the most pertinent at the moment.  Didn't see anything that relates to this immediately, though I'm going to keep looking.  Anybody else have any ideas on how to get this fixed?

---

### Post by williamspajr on 2007-02-11
I'm having a similar problem since updating yesterday (Feb 10 2007)

I get message:

Failed to start the X server (your graphical interface).

It is likely that is not set up correctly.

Would you like to view the X sever output to diagnose the problem.


I did a complete re-install to see if I could pinpoint the problem. 

I then installed my Nvidia driver. The system updated and I restarted. It started normally. 

Auto Updates advised that there were updates available (7). I 
downloaded and installed these, when I restarted I got the same error message as above.

---

### Post by Waappu on 2007-02-11
Hi

This is how I fix my problem. Maybe there is simply way, but this works: 

Type in terminal```
sudo nano /etc/X11/xorg.conf
```
change this line```
Driver		"nvidia"
```
to this```
Driver		"nv"
```
type in terminal```
startx
```
download envy and install it
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.6.1-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.6.1-0ubuntu1_all.deb)
press Ctrl+Alt+F1. Login virtual terminal and type```
envy
```
and install Nvidia driver

---

### Post by Tad2much on 2007-02-11
Great it worked!  Well, sort of.  X starts now, but then instantly crashes and tells me xauth: error in locking authority file /home/jourdan/.Xauthority

tried running 

xauth -b quit 

but to no avail, I still get same problem.

---

### Post by Tad2much on 2007-02-12
Any help on that?  Debating about just nuking .Xauthority and seeing if it gets recreated when x restarts, but not sure.  Any suggestions?

---

### Post by WinterWeaver on 2007-02-12
It's safer to just wait for them to fix the nvidia drivers. I generally don't run the Envy script, as it downloads the binaries from NVidia directly (Last time I used it anyway, which was long ago). 

My suggestion is to just rollback to the default xorg settings. You can do it via:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and in that setup just select your supported card, nv (I don't know if other cards are also affected?)
Select your resolutions, and once it's done,  restart X.

Unfortunately this won't give us nice XGL and fancy other eye candy, but it should work for now, until a proper fix is posted on the forums.

This is working fine for me, and is probably the safest route to take for the moment.

Good Luck,

WW

---

