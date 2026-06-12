---
title: "Ubuntu 11.04 Left mouse button doesn't work?"
date: 2011-05-05
forum: Desktop Environments
---

### Post by nrawlins on 2011-05-05
Hi,

I installed a fresh copy of 11.04 which worked fine until you first login and then the left mouse button fails to work so I can't left click anything.


The right ones is fine? this worked fine on 10 and for the 11.04 installer.


Does anyone have any idea's?

Thanks

---

### Post by Doug Tingle on 2011-05-05
Is it a mouse? Sounds a bit like the Synaptic touchpad problem?...

---

### Post by zalaad on 2011-05-07
Hi,

I have the same problem with 2 different USB mouse (Logitech wireless and Kenginston wired). The left, right and the scroll wheel work sometimes, but most of time they don't. I can always move the mouse though.

I'm using kde4:4.6.2a-ubuntu5.1. I had the problem with -ubuntu5 as well.

I'm using only the keyboard for now, it's very annoying.

Regards,

Zal

---

### Post by wdelv on 2011-05-15
I have had the same intermittent left-mouse-button problem for about a month now.  Sometime I can get it working again after a number of things such as right-clicking in some windows, left-clicking on the top menu-bar drop-downs, Alt-click, Shift-Alt-click or if nothing else - reboot (usually using Ctl-Alt-Del followed by down-arrow to select Restart).
From searching various forums it appears that this has been a fairly wide-spread problem with Ubuntu for a couple of years with no single remedy.
I upgraded from 10.10 to 11.04 in an effort to fix this but the problem still persists.
Does anyone know of a fix, short of installing Fedora?
And, no, it's not a mouse hardware problem.

---

### Post by RowanC on 2011-05-16
I had some wierdness too when upgrading from 10.10 to 11.04 on my netbook - turns out two things went wrong (touchpad stopped working) and left mouse wasn't context sensitive anymore - right clicking always brought up the window menu, and left clicking only moved the window

To fix the mouse issue I changed the compiz window management setting for key to move window - it for some reason defaulted to button1 instead of the usual default <Alt>+Button1.

Works a dream now - I hope you're issue is as simple & random as that to fix.

---

### Post by dirtrider1 on 2011-06-10
I'm having same issue left click doesn't usually work and the mouse will get hung up after a few minutes and this is after a fresh install. The mouse did not even work correctly on the installation cd? I agree with the above poster this is not a hardware problem as my mouse works fine with older Ubuntu versions and Windows and I have tried several install medias to no avail?

---

### Post by jgrocha on 2011-06-14
Same problem here. It is really a "bad user experience", since my external mouse left-click does not work (sometimes). 

$ uname -a
Linux cagliari 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

$ sudo lshw | head
cagliari                  
    description: Notebook
    product: VPCF13Z1E (N/A)
    vendor: Sony Corporation
    version: C606K5MF
    serial: 27527454-5000025
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook family=VAIO sku=N/A uuid=C026D86F-1DF6-DE11-875E-544249E0B573

---

### Post by Rosemachinegun on 2011-07-01
I'm having this problem too.
I installed 11.04 when it came out and in May I began to notice this left clicking problem. I use a Wacom Tablet with mouse and both the mouse's left click and my laptop touchpad left click fail to work. I can left click using my tablet pen, but obviously this is not ideal.
Sometimes it recovers itself in time, but usually I just restart my computer because I don't want to waste my time.

---

### Post by ELMIT on 2011-07-09
Same problem here. It worked for a month without any problem after I upgraded to 11.04, but today no left mouse click anymore.
I rebooted several times, without any luck.

It is definitely not a hardware problem of the mouse, because the internal touchpanel of my EeePC also cannot use the left mouse button anymore.

---

### Post by ELMIT on 2011-07-10
Any news how to solve that problem?
The computer is now nearly useless!

---

### Post by phoenix1/4 on 2011-07-11
Very strange problem indeed... I have experienced similar troubles with two different Logitech wireless keyboard/mouse combos. In my case, it was an older wireless keyboard that still had its controller plugged in that seemed to be the problem. Perhaps this may be a bug that appears when multiple devices are attached (ie. with laptop touch pads AND a wireless mouse?).

EDIT: I did notice this problem after using the back/forward buttons on the side of the mouse.

---

### Post by ELMIT on 2011-07-11
Still not working for me, ... keep the thread on top of the priority, post frequently the progress!

---

### Post by ELMIT on 2011-07-12
I looked up this problem on Google and it seems that it is a well known problem, but no cure,  ...

---

### Post by ELMIT on 2011-07-14
I just got the update notice, ... with right mouse, tab, enter, ... I got the update manager to work, but the left mouse button still does not work.

Any ideas?

---

### Post by leolca on 2011-07-15
I just got a live usb stick with Ubuntu 11.04 and after a few seconds the left button click also stopped working... thanks god I did not install it.

---

### Post by ELMIT on 2011-07-16
Anybody?

---

### Post by ELMIT on 2011-07-18
I still have no solution for that problem found. Anybody?

---

### Post by ELMIT on 2011-07-18
Today it is gone. Maybe that helps to figure out:

I restarted the notebook without my wireless mouse (Logitech) turned on, then the touchpad worked and I could add the mouse again.

Maybe just accident!

---

### Post by kmatr on 2011-07-30
Reload the psmouse kernel module.

sudo modprobe -r psmouse 
sudo modprobe psmouse

---

### Post by levis lover on 2011-08-14
> **kmatr said:**
> Reload the psmouse kernel module.

sudo modprobe -r psmouse 
sudo modprobe psmouse

Total Mouse Failure.
Earlier right click and touchpad were working but now everything has stopped working.

---

### Post by drawkcab on 2011-08-14
I noticed this happened to me during file transfers.  After restarting nautilus functionality is restored.  An annoying bug on all my 11.04 installs.

---

### Post by goofee on 2011-08-15
I have much of the same problem myself. It started on 10.04 actually, so i upgraded to 11.04.

What happens is that when the computer is not use for some minutes, sometimes clicking the left mouse button doesn't work. But if i click the mouse wheel or back button on the mouse, the left button starts functioning again. It's not a hardware issue, this is a really irritating bug.

---

### Post by drhex on 2011-08-18
I've noticed the left-mousebutton problem in 11.04, both 32 and 64-bit.
There was no problem in 10.04 or 10.10.
Usually, I can get the button to work again by pressing all the mouse-buttons and keyboard modifiers one by one.
I tried running "xev" while the system was affected to view input events.
All mouse buttons except the left one generated ButtonPress/ButtonRelease events.  It took a full reboot to get the button back.

---

### Post by drhex on 2011-08-18
Filed a bugreport: [https://bugs.launchpad.net/ubuntu/+bug/828893](https://bugs.launchpad.net/ubuntu/+bug/828893)

---

