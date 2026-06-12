---
title: "New User, flooded with problems"
date: 2009-06-11
forum: General Help
---

### Post by blastbeast on 2009-06-11
Hi all,
I am a new Ubuntu 8.04 (hardy heron) user. I installed it hardly 2 days back.
A couple of hours ago my computer was left idle for some time. When i moved the mouse i saw the resolution had changed by itself. I went into Syetm>Preferences>Screen Resolution, and tried all the combinations possible but none of them was giving me back the default screen resolution that came with the ubuntu installation.
Also after trying one particular screen resolution my monitor went completely black. The only option left was to hit the restart button. 
When the computer restarted i started firefox, and i encountered a few more "bad" problems. When the firefox was on, i couldn't see the taskbar (Applications, Places, System, etc., i dont know what it's called) that appears sitting on the top of the desktop. Also the close,minimize,maximize toolbar of firefox was not visible.
And now the screen keeps blinking constantly.

I am new to Ubuntu, and i liked the first 2 days of my experience with it. But this little turn of events has got me doubting its reliability. Please correct me if I'm wrong. I'm just a noob as far as linux goes.

Please give me solutions to all these problems, and try to be as descriptive as possible, considering I dont even know how to use the command line properly.

Thanks in advance.

---

### Post by blastbeast on 2009-06-11
Also every new application i open(also the computer folder) opens minimized. I mean it doesnt open directly on the screen. 
Help Please :(

---

### Post by elianthony on 2009-06-11
Hi,

First off, you've installed 8.04, have you run all of the updates?

As far as the Firefox problem, it sounds like what you're describing might just be full screen mode. If it is, you can switch between full screen and normal viewing modes by hitting F11 after you open Firefox.

---

### Post by blastbeast on 2009-06-11
Thank you so much. The firefox problem got fixed. 
But, yes i updated my 8.04 after i installed it. There were 384 updates if I remember correctly. 
Any thoughts on the screen resolution problem?

Thanks once again for your quick reply. :)

---

### Post by Magnificence on 2009-06-11
Do you need a driver for your graphic card maybe? :P

Or did it just run perfectly before the resolution went wrong?

---

### Post by elianthony on 2009-06-11
As far as the display problems go, it'd be helpful if you posted your hardware setup, as in what graphics card you're using. Also, did the problem occur after you updated, or made any changes to your system? Oh, and you're welcome.

---

### Post by blastbeast on 2009-06-11
> **Magnificence said:**
> Do you need a driver for your graphic card maybe? :P

Or did it just run perfectly before the resolution went wrong?


Actually the problem started 2 days after i installed the OS.
It seemed to work fine till a couple of hours ago.
But in your opinion which ones and from where should i update my drivers?

Thanks !!

---

### Post by Magnificence on 2009-06-11
I'am still new to Ubuntu, but I know, if you have a NVIDIA or ATI card that you can easly install it through Applications > Add/Remove... and System > Hardware Drivers.

---

### Post by yaroto98 on 2009-06-11
System->Admin->Software Sources

Check all the options, especially the Third Party ones. When you exit and it asks you to reload, say yes.

System->Admin(or preferances, I can't remember)->Hardware Drivers
select your graphics card(with the highest version number) and click enable.

Give it time to download and install the driver. Then reboot.

---

### Post by blastbeast on 2009-06-11
> **yaroto98 said:**
> System->Admin->Software Sources

Check all the options, especially the Third Party ones. When you exit and it asks you to reload, say yes.

System->Admin(or preferances, I can't remember)->Hardware Drivers
select your graphics card(with the highest version number) and click enable.

Give it time to download and install the driver. Then reboot.


I did the Software Sources thing u adviced.
But when i went to Hardware Drivers it displayed "No Proprietary drivers are in use on this system".

---

### Post by Magnificence on 2009-06-11
Why do you have to reboot? It's Linux! ;)

---

### Post by blastbeast on 2009-06-11
> **Magnificence said:**
> I'am still new to Ubuntu, but I know, if you have a NVIDIA or ATI card that you can easly install it through Applications > Add/Remove... and System > Hardware Drivers.

I dont have any graphics card on my machine.

---

### Post by elianthony on 2009-06-11
Enabling those restricted driver's may fix your problem.

---

### Post by blastbeast on 2009-06-11
> **elianthony said:**
> As far as the display problems go, it'd be helpful if you posted your hardware setup, as in what graphics card you're using. Also, did the problem occur after you updated, or made any changes to your system? Oh, and you're welcome.

Ubuntu
Release 8.04 (Hardy)
Kernel Linux 2.6.24-24-generic
GNOME 2.22.3

Hardware
Memory: 2.0 Gib
Processor 0: Intel(R) Core(TM)2 Duo CPU E4600 @ 2.40GHz
Processor 1: Intel(R) Core(TM)2 Duo CPU E4600 @ 2.40GHz

Sorry for the late reply I had to write this down manually.

---

### Post by blastbeast on 2009-06-11
> **elianthony said:**
> Enabling those restricted driver's may fix your problem.

Ok. The update is going on. Still 10 minutes remaining.

---

### Post by blastbeast on 2009-06-11
Installing the restricted drivers didnt help. :(

---

