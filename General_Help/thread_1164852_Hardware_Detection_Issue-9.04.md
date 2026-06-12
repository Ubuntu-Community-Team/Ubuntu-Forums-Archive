---
title: "Hardware Detection Issue-9.04"
date: 2009-05-20
forum: General Help
---

### Post by ASE0507 on 2009-05-20
I'm a long time user first time poster. I've been using ubuntu for a few years now but up until now I've been able to find resolutions to every issue that I've ran into, graphical, audio, software, wine, everything.

I'm running Ubuntu 9.04 and for some reason its not detecting my video capture card, or its at least not listing it under lspci or when I run xrandr.

I have a Lifebook N6410 with a Radeon Mobility X1400 graphics card, Intel Core 2 Duo Processor 1.6ghz, 1GB of RAM but for the life of me I can't find the manufacturer of the video capture card, I'm not sure if its integrated or not. I know its worked before because I was able to capture some video a friend and I shot and uploaded it, but that was back when I was dual-partitioned Windows XP Media and Ubuntu 7.10 (didn't try and get it working in Ubuntu until now)

I would just like to have some information so I can see if there's even a chance that it may or may not be supported for mythtv or for video capture or anything else for that matter.

any other information you want or need, please let me know. Thanks in advance.

---

### Post by ASE0507 on 2009-05-22
bump.

I just downgraded down to 8.10 because I was annoyed with the graphics issues I was having plus wine was giving me way more trouble than it ever has and it worked just fine in 8.10.

Problem Persists however, lspci doesn't list the capture card, however there are slots where I think it might be located, but not being recognized or something 

lspci excerpt
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 21)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```Thinking it might be at PCI location 03:00.0 or 04:00.0. since the analog switch to turn off the wireless internet is rather close in proximity to the video capture card and could be between it (I realize physical location and digital location don't necessarily relate but its a possibility)

any ideas anyone?

---

### Post by ASE0507 on 2009-05-27
bump

---

### Post by ASE0507 on 2009-06-19
Thanks for the help... never gotten a response on here 2 years ago, and this year as well it seems (different login, but forgot it since it was so long ago hence the bean count being so low)

at any rate, I found it... lsusb listed it as AverMedia MPEG-2 capture device... so it was connected through an internal usb instead of it being a pci slot in the laptop.

now if only I could get my keyboard to work on my original hard drive's install of ubuntu and not just only on the live cd or the install on my external... 

closed

---

