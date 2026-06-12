---
title: "Getting the correct DPI ?"
date: 2009-05-09
forum: General Help
---

### Post by Yankee_Fan on 2009-05-09
Hi. I am running Jaunty on my HP dv4 laptop. I am trying to get my DPI set correctly on my laptop.  My video card is listed as "Mobile Intel® GM45 Express Chipset"  The default was set at 96 dpi.

I ran the following commands:

```
mike@mike-laptop:~$ xdpyinfo | grep dimensions
  dimensions:    1280x800 pixels (304x190 millimeters)
mike@mike-laptop:~$ xdpyinfo | grep resolution
  resolution:    107x107 dots per inch
```
and added the following line to my xorg.conf file in the "Monitor" section:

```
	DisplaySize	304 190
```
After re-booting my Xorg.0.log shows the wrong DPI. I was expecting it to say 107, 107 but instead this is what I have:

```
(**) intel(0): Display dimensions: (304, 190) mm
(**) intel(0): DPI set to (171, 273)
```

Is there some setting that I am missing to get it to the correct (107,107) DPI???

---

### Post by HavocXphere on 2009-05-09
I think that if your resolution is set correctly, i.e. at the panel's native resolution then the DPI will naturally be correct.

Might be wrong in this though..

---

