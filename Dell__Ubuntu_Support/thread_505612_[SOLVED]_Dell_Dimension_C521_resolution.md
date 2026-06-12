---
title: "[SOLVED] Dell Dimension C521 resolution"
date: 2007-07-20
forum: Dell  Ubuntu Support
---

### Post by tman4343 on 2007-07-20
I recently bought a Dimension C521 from dell that had windows xp on it.  I replaced the hd with a new 300 gig sata hd and put Ubuntu 7.04 on it.  It seems to be working great, except the screen resolution is painfully low.  When going to System->Preferences->Screen Resolution i can only choose between 800x600 and 640x480.  I have read [this]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-aebd81e5fe762bccb1b7e4d7a10ed7a1276aa634")  tried to do those fixes, none have worked.  I tried downloading newer drivers from the nvidia website, but that failed also (on startup the xorg crashed and it booted me into command prompt).  I restored the xorg.conf file to the original and got it up and running again, but i am still stuck with the low resolutions.  I have looked at the xorg.conf file and it shows the resolutions that i want...including 1280x1024(my ideal resolution) in the list.  So I don't think there is something that should be changed in that file. I tried running sudo nvidia-settings and that opened the nvidia display manager.  But no where on there did it let me change the resolution.

The monitor is a Dell E197EP 19'' flat monitor
The comp has a NVIDIA GeForce 6150 LE onboard graphics
I'm using an amd 64 bit proccessor (not 100% sure of the speed, but i don't think that matters)

The computer was running in 1280x1024 resolution in windows before i switched out he hd and installed ubuntu, so i know the system can handle it.

I am fairly new to linux and am not sure what do at this point.  If anyone can give me some suggestions it would be greatly appreciated.

---

### Post by teotwawki on 2007-07-20
I had the same problem and was able to solve by editing /etc/X11/xorg.conf file and adding the HorizSync and VertRefresh entries to the Monitor Section. Here is the whole section w/ my additions. NOTE: I have a DELL 1907FP monitor and your settings may need to be different. Check w/ the display manufacturer for the appropriate Horiz/Vert ranges.

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Hope this helps...

---

### Post by tman4343 on 2007-07-23
That worked great teotwawki.  Thanks for the quick and accurate reply.

---

### Post by resume-writer on 2007-09-14
Though I have the same system that you do (and the same problem), and wasn't able to locate a /etc/X11/xorg.conf file. Is there another location perhaps?

---

### Post by resume-writer on 2007-09-14
Actually, I just realized that I have a different monitor than you, so I'll do some research and find out the file name from my manufacturer. Thank you for posting you problem: it sure helps me.

---

