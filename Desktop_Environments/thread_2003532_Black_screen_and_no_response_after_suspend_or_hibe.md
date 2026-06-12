---
title: "Black screen and no response after suspend or hibernate"
date: 2012-06-14
forum: Desktop Environments
---

### Post by Mr LJ on 2012-06-14
Since installing Ubuntu 12.04 my system is unable to suspend or  hibernate correctly. Putting the computer to stand-by and copying the  ram to the disk seems to work, but when resuming it ends up with a black  screen (monitor even turns of after several searches for input). 

The computer does not respond to any shortcut - or at least I cannot see  anything. I will try to log in via ssh later.  
In launchpad a similar  problem is listed, but refers to a issue with the AMD graphic driver.  However I'm using a NVIDIA Geforce 7600GT. Installing the newest Ubuntu kernel updates and nvidia-driver has no effect.
I  prior used the latest release of Linux Mint with Mate; there were no  problems at all - asides from a GUI that still needs some fixes in  detail.   
In the pm-suspend.log I cannot find any   abnormality, only  the network-manager seems unable to put all processes to sleep.  

Here some information about the system: 
Linux  3.2.0-25-generic  #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64  GNU/Linux 
NVIDIA Driver Version 295.49 X Server 11.0, Version 1.11.3  (11103000) Dual monitor 2x HP2309 as TwinView, connected to HDMI and  DVI.
The pm-logfiles are attached

Is this problem already known and are there any ways to solve it?
Thanks in advance
LJ

---

### Post by Frogs Hair on 2012-06-14
I have Win 7 dual boot and in the past have had to use the power button to awaken from sleep/suspend.The keyboard and mouse will not work to wake the computer in Ubuntu as they do in Windows.

Hard restart is not needed, but I do have to depress the power button slightly and the computer awakens. I have no need to hibernate, so I can't address that. Search for other threads on this problem because I have seen it posted before.

---

### Post by Mr LJ on 2012-06-14
the system restarts after pressing the power button, but afterwards I got the black screen. 
When resuming from hibernation I see the boot screen however the screen  turns black after the ubuntu boot splash (the colored screen).

Differing from the other threads I have no problems with logging in or out (from unity).
The screen stays black for a second and then the desktop is back again.
I also have no problems with installing the nvidia driver -  open gl and even games run smooth.

Edit: when the screen is black, neither ssh nor ping works

Edit2: Just updated to 3.2.0-26 kernel, but still no change

---

### Post by sauthess on 2012-06-17
I all,

I have sometimes the same problem on optimus enabled laptop (but using only intel card).

It suspend/resume without problem few times and without reason another suspend breaks and I have a black screen...

I can switch to ctrl-alt-F1 and restart lightdm (service lightdm restart) and X restart without problem but I have lost my opened programs...

Annoying...

If someone have an idea...

Thanks in advance,

BR

---

