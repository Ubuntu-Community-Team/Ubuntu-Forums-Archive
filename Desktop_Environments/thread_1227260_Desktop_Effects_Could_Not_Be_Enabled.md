---
title: "Desktop Effects Could Not Be Enabled"
date: 2009-07-30
forum: Desktop Environments
---

### Post by Firestar292 on 2009-07-30
Hi, Im new to ubuntu and I keep getting this error message Desktop effects could not be enabled when I try to set my compiz visual effects up to Normal or Extra.  When I type in compiz in terminal I get this 

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity
```Not sure what the problem is, any help would be appreciated, thanks.

---

### Post by wojox on 2009-07-30
Go to System > Administration > Hardware Drivers

See if there is a driver for your graphics card that needs to be enabled.

---

### Post by Firestar292 on 2009-07-30
Nope, no graphics drivers there.

---

### Post by wojox on 2009-07-30
Open a terminal and post back the output of:

```
sudo lshw -C video
```

---

### Post by Firestar292 on 2009-07-30
```
 *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```

---

### Post by wojox on 2009-07-30
Back up your xorg.conf file and add this:

```
Section “Device”
Identifier “Intel Corporation Mobile Integrated Graphics Controller”
Driver “intel”
# Driver “i810&#8243;
BusID “PCI:0:2:0&#8243;
EndSection

Section “Monitor”
Identifier “Generic Monitor”
Option “DPMS”
HorizSync 28-64
VertRefresh 43-60
Option “MonitorLayout” “CRT,LFP”
Option “Clone” “true”
EndSection 
```

After disabling the “cloning” of screens in the “Screen Resolution” settings of Ubuntu you should be all set.

---

### Post by Firestar292 on 2009-07-30
How do I backup that file? And with the code, do I just put that in the terminal? 
Sorry for all the questions, im new, I really appreciate the help.

---

### Post by Mia1990 on 2009-07-30
Try compiz check from this [link]("http://forlong.blogage.de/entries/pages/Compiz-Check") and post that.You have a intel card check the link at the bottom of my post for compiz blacklisted cards.

---

### Post by Firestar292 on 2009-07-30
```
 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)
```

Thats what I got, and it doesnt seem to be blacklisted.

---

### Post by Mia1990 on 2009-07-30
ok now go to synaptic and see if emerald is checked try to use that for rendering.

---

### Post by Firestar292 on 2009-07-30
ok I got emerald checked and applied, now what do I do?

---

### Post by Mia1990 on 2009-07-30
does compiz run now because that was the only error i seen you may have to reboot

---

### Post by Mia1990 on 2009-07-30
oh i forgot to ask and i didn't see it but you installed compizconfig-settings manager didn't you

---

### Post by Firestar292 on 2009-07-30
It didnt run, but ill reboot and try and again

---

### Post by Firestar292 on 2009-07-30
Ok I rebooted, and it still doesnt work.  And yes, I installed that.

---

### Post by Mia1990 on 2009-07-30
Do you know what graphics driver your using try to find that out because that is about all i would know that it could be.

---

### Post by Firestar292 on 2009-07-30
No idea what driver I am using, Ill keep looking but do you know where I could find what one I am using?

---

### Post by Mia1990 on 2009-07-30
you've already looked in hardware drivers so try synaptic sorry i couldn't be any more help

---

### Post by Firestar292 on 2009-07-30
Well it looks like I have the right one.

---

### Post by Mia1990 on 2009-07-30
you found it?Try doing a search for that driver and compiz and see what it comes up with

---

### Post by Firestar292 on 2009-07-30
ok, well theres still no rendering, so I dont know if that means the emerald doesnt work or something. 

```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)
```

---

### Post by Mia1990 on 2009-07-30
did you skip the blacklist check when you ran compiz check if you did i guess go ahead and run it you can't run compiz anyway and it will tell you if your card is blacklisted.

---

### Post by Firestar292 on 2009-07-30
Nope im not blacklisted.

---

### Post by Mia1990 on 2009-07-30
just going over all the things to make compiz run.Have you changed visual effect's.

---

### Post by Firestar292 on 2009-07-30
The visual effects is stuck on None, I cant change it to Normal or Extra...thats where I get the error.

---

### Post by Mia1990 on 2009-07-30
The visual effects require hardware acceleration as well as supported drivers do a google search and see what driver you need.

---

### Post by Firestar292 on 2009-07-30
I cant seem to find any accelerators, this is difficult.

---

### Post by ellalan on 2009-07-30
Have you tried installing simple-ccsm in synaptics? If not try that because I remember "simple-ccsm" enabled visual effects once for me.

---

### Post by Firestar292 on 2009-07-30
I just tried that, thanks.  But no it still does not work, im pretty sure it has to do with needing a rendering method.  

```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)
```

---

