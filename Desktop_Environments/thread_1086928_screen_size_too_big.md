---
title: "screen size too big"
date: 2009-03-04
forum: Desktop Environments
---

### Post by lozzy on 2009-03-04
hi.. im totally new to ubuntu.... and my screen resolution is way too big.... cant get anything other than i think its 960x600 (16.10)??? 
i am no expert and dont know what to do as i need to get the screen size smaller so can anyone help me in the simplest way possible??? please ??

thanks

---

### Post by NoReflex on 2009-03-04
Hello!

What video card do you have (ATI, nVIDIA, Intel)?
I have a nVIDIA 8600 mobile on my notebook and I use nvidia-settings to change resolution, multiple monitors etc.
You should install the proprietary driver for your video card. Just go to System -> Administration -> Hardware drivers and see what drivers are available.

Best wishes,
NoReflex

---

### Post by lozzy on 2009-03-05
> **NoReflex said:**
> Hello!

What video card do you have (ATI, nVIDIA, Intel)?
I have a nVIDIA 8600 mobile on my notebook and I use nvidia-settings to change resolution, multiple monitors etc.
You should install the proprietary driver for your video card. Just go to System -> Administration -> Hardware drivers and see what drivers are available.

Best wishes,
NoReflex

there are none there ??:(

---

### Post by NoReflex on 2009-03-05
Ok.

Let's start over.
First we have to identify your video card. To do this open up a terminal and write ```
lshw -C video
```
then post the result here.
You could also post some other details of your system that could help:
- CPU
- RAM
- Which Ubuntu (or other Linux) version you have
- Motherboard model
The commands to find these out are **lshw -C x** (where x is the category you want informations on - cpu, memory etc.) and **lspci**.

Best wishes,
NoReflex

---

### Post by lozzy on 2009-03-05
> **NoReflex said:**
> Ok.

Let's start over.
First we have to identify your video card. To do this open up a terminal and write ```
lshw -C video
```
then post the result here.
You could also post some other details of your system that could help:
- CPU
- RAM
- Which Ubuntu (or other Linux) version you have
- Motherboard model
The commands to find these out are **lshw -C x** (where x is the category you want informations on - cpu, memory etc.) and **lspci**.

Best wishes,
NoReflex

i got this when i put in the first instruction

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 65x/M650/740 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_palette cap_list
       configuration: latency=0

---

### Post by NoReflex on 2009-03-05
I don't have any experience with those card models on Linux. I googled a bit and it seems that there is no 3D acceleration available on those cards.
[http://www.mail-archive.com/debian-laptop@lists.debian.org/msg16796.html](http://www.mail-archive.com/debian-laptop@lists.debian.org/msg16796.html)
Maybe someone else can give you a hand with it.

Best wishes,
NoReflex

---

### Post by hictio on 2009-03-05
Independently of the 3D drivers, lozzy, do you know that your monitor can perform to a higher resolution than the one you are having right now?

Is this a laptop, or a desktop machine?

There is another thing you can try, to get the maximum resoution, and that is editing your '/etc/X11/xorg.conf' file to use the higher resolutions, but for that you'll need to provide the info or specs of your monitor.

---

### Post by lozzy on 2009-03-06
> **hictio said:**
> Independently of the 3D drivers, lozzy, do you know that your monitor can perform to a higher resolution than the one you are having right now?

Is this a laptop, or a desktop machine?

There is another thing you can try, to get the maximum resoution, and that is editing your '/etc/X11/xorg.conf' file to use the higher resolutions, but for that you'll need to provide the info or specs of your monitor.

hi.. please tell me how to find corect info?? as im clueless?? thanks 

ps this resolution size is drivin me mad .....:o

---

### Post by hictio on 2009-03-06
> **lozzy said:**
> hi.. please tell me how to find corect info?? as im clueless?? thanks 

ps this resolution size is drivin me mad .....:o

What it is the machine you are using Ubuntu on? A laptop, or a desktop?
You'll need, first of all, getting the technical specs of the monitor you are using, specifically, the vertical and horizon refresh rate.

Identify your monitor, maker & model, and search for those two values on Google, and then post back.

---

### Post by lozzy on 2009-03-11
> **hictio said:**
> Independently of the 3D drivers, lozzy, do you know that your monitor can perform to a higher resolution than the one you are having right now?

Is this a laptop, or a desktop machine?

There is another thing you can try, to get the maximum resoution, and that is editing your '/etc/X11/xorg.conf' file to use the higher resolutions, but for that you'll need to provide the info or specs of your monitor.

hi..

monitor is videoseven h17ps?? 17" TFT LCD 1280x1024 
SXGA Pixel Pitch 0.264 mm Display Colours 16.7 Million Brightness 370 cd/m2 Contrast Ratio 350:1 Viewing Angle 140 (h) 130 (v) Response Time 8 m/sec Horizontal Scan Rate 31 - 81Khz Vertical Scan Rate 56 - 75Hz Input Connector Mini 15pin D-sub
Safety Certificates CE, UL, FCC, VCCI
Dimensions (WxDxH) 381 x 199 x 426 mm Vesa Wall Mounts 75mm

---

### Post by hictio on 2009-03-15
Please, post your /etc/X11/xorrg.conf file, so I can take a look at it, and add the values for your monitor.
To post it, do this to copy it, type this onto a Terminal:

```

cp /etc/X11/xorg.conf ~/Desktop/xorg.txt ENTER

```

This will copy the file as 'xorg.txt' on your Desktop, open it with a double click, select all, copy, and then paste that onto another post of this thread.

---

