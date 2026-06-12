---
title: "tvtime and beryl"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by sir_skiner on 2007-07-24
i tried gstreamer-properties setting to use x11 (no xv) extension instead of xv which affected on playing movies only. tvtime doesn't run. it gives me following error:

```
    Cannot allocate enough off-screen video memory.  This may be fixed by:

      1. Closing or restarting large X applications.
      2. Lowering the input width of tvtime (--inputwidth parameter).
      3. Lowering your colour depth or highest configured resolution.
      4. Increasing the amount of video memory in your X config file
         (for example, if you are using the i810 XFree86 driver.)

```
none of proposed steps works, exept exiting beryl. runnig xawtv --noxv works, but picture i get is ugly. what to do?

the system is fiesty 7.04 with xorg intel video driver managing g965 intel video device.

---

### Post by silverbyte on 2007-09-04
I had similar issues / not only with TVTIME but with MOVIE PLAYER (totem) when playing MP3's with visual effects or RYTHM BOX playing visual effects.... 

- tvtime gave me the exact same message you got
- movie player gave me an error about allocated memory issues / etc. 

so i searched the internet to read about allocated memory problem + nvidia + amd64 and found this.

---------------------------------------------------------
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/README.txt](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/README.txt)
---------------------------------------------------------
Chapter 10. Allocating DMA Buffers on 64-bit Platforms

NVIDIA GPUs have limits on how much physical memory they can address. This
directly impacts DMA buffers, as a DMA buffer allocated in physical memory
that is unaddressable by the NVIDIA GPU cannot be used (or may be truncated,
resulting in bad memory accesses).
---------------------------------------------------------

SMALL STORY SHORT / I in that article i read this 

---------------------------------------------------------------------------------
On AMD's AMD64 platform, the size of the IOMMU can be configured in the system
BIOS 
----------------------------------------------------------------------------------

Then i said to myself... hmmmm the bios has video memory option in it.. i wonder whats its set too.... I went ot my bios and my system memory was 16megs.... i changed it to 128megs... started ubuntu with compiz fusion AND VOILA!!! IT WORKS!

TVTIME / MOVIE PLAYER / everything with visual effects worked... Thats my guess... hope it helps you out. 

My system is: 
AMD64 X2 4ghz
onboard nvidia 6150
1ghz ram

---

