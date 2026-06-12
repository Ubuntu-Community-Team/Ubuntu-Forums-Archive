---
title: "Dual monitors"
date: 2010-04-01
forum: Desktop Environments
---

### Post by leneflower on 2010-04-01
So I just installed KUbuntu. I'm not a total Linux noob, but some things are done differently in Ubuntu, so I guess I'll have a couple of questions in the near future.

Here's the first. I have a NVidia graphics card and two differently sized monitors. X starts up with the same image on both monitors, in the same resolution, giving me a headache when I look at the bigger monitor because it's blurred. There is [this thread]("http://kubuntuforums.net/forums/index.php?topic=3107874.0") on the kubuntu forums, describing how to use dual monitors, but it requires starting and setting the orientation and size of the monitors every time after you log in. I'm looking for a permanent solution, so I don't have to do this every time. How would I do that?

TIA
Lene

---

### Post by Grenage on 2010-04-01
I'd recommend using nvidia-settings to configure the displays, be it via TwinView or separate X displays.

---

### Post by leneflower on 2010-04-01
I have to take a quick detour about installing NVidia drivers. I installed nvidia-settings and nvidia-current (why is nvidia-current not a dependency of nvidia-settings, btw?) and ran nvidia-xconfig, but starting X failed because the nvidia kernel module was missing. When I tried:
[FONT=Fixedsys]sudo modprobe nvidia

[/FONT] I got:
[FONT=Fixedsys]FATAL: Error inserting nvidia_current (/lib/modules/2.6.32-18-generic/updates/dkms/nvidia-current.ko): No such device
[/FONT]
What have I missed?

Greets, Lene

---

### Post by leneflower on 2010-04-01
By the way, KRandRTray works as well to configure dual monitors, even without NVidia drivers. But it doesn't keep its state across logins, or rather it kills the KDE session on login if dual monitors are enabled - then the next session starts with RandR disabled (luckily ;-) ).

I'd rather use the NVidia drivers though, because I'll need them anyway.

---

### Post by Grenage on 2010-04-01
I've not used nvidia-current before.  I am assuming you have installed the Nvidia drivers?

System/Administration/Hardware Drivers.

---

### Post by leneflower on 2010-04-01
Sorry for being dumb, but...

> **Grenage said:**
> I've not used nvidia-current before.  I am assuming you have installed the Nvidia drivers?I thought nvidia-current *were* the NVidia drivers...
> **Grenage said:**
> System/Administration/Hardware Drivers.That seems to refer to Ubuntu, not KUbuntu, right? I can't find anything like this in KUbuntu. Any idea how I can find this?

---

### Post by Grenage on 2010-04-01
They may well be, I've just never installed them from the CLI.

I'm so used to just clicking on 'new posts' that I didn't even realise you were running Kubuntu!

---

### Post by GepettoBR on 2010-04-01
> **leneflower said:**
> why is nvidia-current not a dependency of nvidia-settings, btw?

There are older versions of the nVidia driver available in the repos that also work with nvidia-settings. for people who use those, it would be pointless and cumbersome to also have to install the current drivers just to use the settings package.

> **leneflower said:**
> That seems to refer to Ubuntu, not KUbuntu, right? I can't find anything like this in KUbuntu. Any idea how I can find this?

The difference between Ubuntu and Kubuntu is merely what DE (GNOME or KDE) they use. As far as hardware drivers are concerned, there is no difference between them.

---

### Post by northking on 2010-04-18
I am new to Ubuntu, so forgive me if I state the obvious. On my desktop the menu choice System/Administration/Hardware Drivers (let it run) offers 2 nvidia drivers, 173 and 185 (recommended). I installed the 185 and it includes the nvidia-settings in the package, which shows up in the menus as System/Administration/NVIDIA X Server Settings. 

I have a GeForce 9600 GSO card with 2 DVI ports and 2 monitors connected. In the above mentioned control panel (sorry, I know that's Microsoft speak) I select X Server Display Configuration. The second monitor is disabled by default. Select it, configure for TwinView (my choice), change resolution to Auto (or whatever), and set Position to something other than Absolute (having 2 monitors set to absolute is not recommended). Click Apply and wait. Voila! 

My problem is when I select Save to X Configuration File I get the error "Failed to parse existing X config file '/etc/X11/xorg.conf'". Every relog, restart, etc. I have to redo the settings. I am guessing this is a permissions problem, that is, nvidia-settings doesn't have write permission for that folder or file. I have tried various hacks with no favorable results (some requiring me to restart in recovery mode as root and remove the xorg.conf file and  letting the system default). 

Hope this is at least informative if not useful.

-Dave

---

### Post by cascade9 on 2010-04-18
> **northking said:**
> My problem is when I select Save to X Configuration File I get the error "Failed to parse existing X config file '/etc/X11/xorg.conf'". Every relog, restart, etc. I have to redo the settings. I am guessing this is a permissions problem, that is, nvidia-settings doesn't have write permission for that folder or file. I have tried various hacks with no favorable results (some requiring me to restart in recovery mode as root and remove the xorg.conf file and  letting the system default). 


sudo nividia-settings should let you keep your settings ;)

---

### Post by GepettoBR on 2010-04-18
> **cascade9 said:**
> sudo nividia-settings should let you keep your settings ;)

and risk corrupting your config files. For graphical applications, use gksudo instead of sudo. ;)

---

