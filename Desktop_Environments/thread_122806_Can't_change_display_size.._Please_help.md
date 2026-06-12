---
title: "Can't change display size.. Please help"
date: 2006-01-28
forum: Desktop Environments
---

### Post by chugru on 2006-01-28
Hi, all...

I'm trying to learn my way around Kubuntu, but I'm having a few problems.

My display screen size is set at 640x480 @ 60 Hz, and the dropdown list in KDE's  "Configure - Desktop" shows no other options. I would like it to be 1280x1024 @ 72 Hz.

What must I do to change it??

Thanks... :D

---

### Post by gingermark on 2006-01-28
Do you know what graphics card you have? I expect it's a driver issue, although I am far from an expert in such matters. Still, posting the make and model of your graphics card should allow others to help you better.

---

### Post by chugru on 2006-01-28
gingermark wrote:

"Do you know what graphics card you have?"

My lshw shows the following:
*-display:0 
----description: VGA compatible controller 
----product: RV280 [Radeon 9200 SE] 
----vendor: ATI Technologies Inc 
----physical id: 0 
----bus info: pci@01:00.0 
----version: 01 
----size: 128MB 
----width: 32 bits 
----clock: 66MHz 
----capabilities: vga bus_master cap_list 
----resources: iomemory:c8000000-cfffffff ioport:b800-b8ff iomemory:d5ef0000-d5efffff ir q:5 
*-display:1 UNCLAIMED 
----description: Display controller 
----product: RV280 [Radeon 9200 SE] (Secondary) 
----vendor: ATI Technologies Inc 
----physical id: 0.1 
----bus info: pci@01:00.1 
----version: 01 size: 128MB 
----width: 32 bits 
----clock: 66MHz 
----capabilities: bus_master cap_list 
----resources: iomemory:c0000000-c7ffffff iomemory:d5ee0000-d5eeffff

I hope this helps... I don't even know why the graphics card should show twice!

---

### Post by gingermark on 2006-01-28
To be honest, I know very little about this topic. Hopefully someone else can help you.

If it is a driver issue, I know Seveas' repository has a load of ATI drivers, as detailed [here](http://mirror2.ubuntulinux.nl/dists/breezy-seveas/drivers/), but I have no idea which, if any, would be suitable.

Sorry I couldn't be more help.

---

### Post by obibok on 2006-01-29
What monitor do you use? Set **HorizSync** and **VertRefresh** according to your monitor specs in */etc/X11/xorg.conf*

example:
```
Section "Monitor"
        Identifier      "Monitor"
        Option          "DPMS"
        # default H 28-64
        HorizSync       **28-81**
        # default V 43-72
        VertRefresh     **43-76**
EndSection
```

---

### Post by chugru on 2006-01-29
**obibok...**

I use a Dell P991 CRT. I added HorizSync & VertRefresh rates as suggested.

Voila! Works great, now!!

Thanks for the suggestion... You just became my best friend!

---

