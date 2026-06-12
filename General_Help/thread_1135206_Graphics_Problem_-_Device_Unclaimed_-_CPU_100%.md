---
title: "Graphics Problem - Device Unclaimed - CPU 100%"
date: 2009-04-24
forum: General Help
---

### Post by slibuntu on 2009-04-24
Hi guys, 

I'm running 9.04 at the moment and am having one problem that is driving me mad, my CPU is spiking very regularly because it is being forced to handle graphics duties. Scrolling web pages and changing windows or workspaces is painful 

Here's the o/p of lshw -c video

```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: ES1000
       vendor: ATI Technologies Inc
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=66 mingnt=8

```


My xorg.conf file is very small - here it is - 
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```


Does anyone know how I can get the graphics card to work and give my CPU a rest!


==Update==
I just checked 'Hardware Drivers' to make sure there weren't any there, there aren't

---

### Post by slibuntu on 2009-04-24
Hate to be a selfish bumper, but here goes... Anyone?

---

### Post by slibuntu on 2009-04-27
I had a check back with Ubuntu 8.04 by booting into a live USB. The scrolling isn't as bad, and the spike in CPU isn't the same. 

Is it possibe to rollback/revert my graphics drivers to the old ones so that they might accept this very old card?

The driver in 8.04 is 1:6.8.0-1 and the one in Jaunty is 1:6.12.1-0ubuntu2

It's the xserver-xorg-video-ati driver

---

