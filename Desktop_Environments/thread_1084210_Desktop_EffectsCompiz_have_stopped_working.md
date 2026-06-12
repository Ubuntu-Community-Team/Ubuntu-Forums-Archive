---
title: "Desktop Effects/Compiz have stopped working"
date: 2009-03-01
forum: Desktop Environments
---

### Post by alisonnic on 2009-03-01
A problem with Desktop Effects/Compiz cropped up today when I booted. I have been using "Extra" Visual Effects, four Workspaces, and Compiz special effects, but today upon booting I had only two Workspaces and Visual Effects had been reset to None.

Adding back the two Workspaces was easy but I haven't been able to get special desktop effects back. 

I've tried switching Extra Visual Effects back on (by right-clicking on the desktop and choosing Change Desktop Background, then Visual Effects and clicking the Extra radio button) but this fails. I get two popups in succession. First:

  > Searching for available drivers

The screen goes blank for a moment, then the desktop returns and a second popup appears with this message:

  > Desktop effects could not be enabled

I've tried deactivating and then re-installing the nVidia driver (System->Administration->Hardware Drivers) but this made no difference. I'm running the NVIDIA driver version 177 and it shows as activated and currently in use.

I installed compiz-settings-manager a couple of weeks ago and enabled the cube and assorted effects with no problem. Since then, the only thing I've changed on this machine that I can imagine might have an impact on the desktop was to install VirtualBox (first the OSE version and then the PUEL version).  

I've also installed Firefox, Thunderbird, xpdf, Foxit Reader, and a printer driver since I started using compiz, but it's hard to see how any of these might be affecting the desktop's ability to detect the nVidia drivers. One other thing I did was switch from a 1024x768 monitor to a 1360x768 monitor, but Compiz and Extra Visual Effects were working fine on this (as was VirtualBox) when I last booted the machine a few days ago.

Any suggestions for a fix? :confused:

--------------

Here's my system configuration:


Asus A7N8X Deluxe
AMD Athlon XP 3000+ Barton
1 GB RAM (2x512)
EVGA GeForce 6800XT
300 GB SATA hard drive
Asus DVD burner
floppy
Thermaltake 430W
KDE monitor, 1360x768
  (60 Hz in System->Administration->NVIDIA X Server Settings but
   52 Hz in System->Preferences->Monitor Resolution Settings; 
   the monitor itself reports 60 Hz.)

Ubuntu 8.10
Kernel Linux 2.6.27-11-generic
GNOME 2.24.1
NVIDIA driver version: 177.86
X Server version Number: 11.0

-----

compiz check returns these results:
Checking for Xgl: present. 
Checking for nVidia: present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

After this, compiz check hangs X and I have to log out and log back in to recover. :(

---

### Post by overdrank on 2009-03-01
> **alisonnic said:**
> 

  
I've tried deactivating and then re-installing the nVidia driver (System->Administration->Hardware Drivers) but this made no difference. I'm running the NVIDIA driver version 177 and it shows as activated and currently in use.



Hi and are you able to use the nvidia-settings ```
gksu nvidia-settings
```
and you may look at [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by hictio on 2009-03-02
I had a similar problem while I was using 8.04, even running compiz-check gave me errors, but, after issuing it, and executing:

```

compiz --replace ccp & emerald --replace & ENTER

```

Got the Desktop Effects back, you can read about it here: [Vanishing plugin](http://oesediez.blogspot.com/2008/10/vanishing-plugin.html)

---

### Post by alisonnic on 2009-03-02
> **overdrank said:**
> Hi and are you able to use the nvidia-settings ```
gksu nvidia-settings
```
and you may look at [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070")

Yes, gksu nvidia-settings brings up the same GUI as System->Administration->NVIDIA X Window Settings, and yes, it runs fine.

compiz check fails; see the log at the end of my original post.

---

### Post by alisonnic on 2009-03-02
> **hictio said:**
> I had a similar problem while I was using 8.04, even running compiz-check gave me errors, but, after issuing it, and executing:

```

compiz --replace ccp & emerald --replace & ENTER

```

Got the Desktop Effects back, you can read about it here: [Vanishing plugin](http://oesediez.blogspot.com/2008/10/vanishing-plugin.html)

Thanks for the tip! I tried executing your command (after reading the Vanishing Plugin post). I had to install the emerald package, but after I did so, the compiz command fails anyway:

> alison@Auburn:~$ compiz --replace ccp & emerald --replace &
Checking for Xgl: [6] 6465
[7] 6467
alison@Auburn:~$ present. 
Checking for nVidia: present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

[5]   Done                    emerald --replace


*Update:* I reran the compiz & emerald command, this time preceded by sudo, and didn't get the error messages quoted above. However, I still can't turn on Normal or Extra Visual Effects. :confused:

---

### Post by alisonnic on 2009-03-27
This problem has remained unsolved. 

Regretfully, I've decided to pull the plug on my Ubuntu experiment and rebuild the machine with XP Pro. Details here:

[http://ubuntuforums.org/showthread.php?p=6968825#post6968825]("http://ubuntuforums.org/showthread.php?p=6968825#post6968825")

Thanks to everyone here who made suggestions.

---

