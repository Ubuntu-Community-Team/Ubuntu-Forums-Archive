---
title: "E1505n no video signal"
date: 2007-10-09
forum: Dell  Ubuntu Support
---

### Post by Mlehliw on 2007-10-09
Suddenly my laptop decided to stop sending a video signal to the display for some reason. It was working fine, then I had to go to a different building so I powered it off and put it in my backpack. When I turned it on again, everything was normal except there was no video to speak of. The backlight turns on and I know the computer is generally working since I can hear the logon music and I can actually logon and turn on amarok just by using the shortcuts.

I think I'm pretty careful with my laptop, I'm not rough housing it or anything. I guess I'll have to call dell about this, but I won't be able to do so for several hours so I was wondering if this has happened to anyone else before or maybe they know what would have happened. I am using the geforce go 7300. Thanks.

---

### Post by pbcartwright on 2007-10-09
are you sure you didn't get a kernel update ?? Do you have more kernel choices in your grub boot loader? The NVIDIA cards need the drivers reconfigured every time you do an update..
can you do CTRL-ALT-F1 to get to a text login? if so, go to /etc/X11 and edit xorg.conf and change your video driver to  "nv" from nvidia.
download & install ( aptitude install?) envy, which is a wonderful tool to setup your NVIDIA adaptors.

---

### Post by Mlehliw on 2007-10-09
No this is definitely a hardware problem. The monitor never displays anything from when I boot it up. So I can't see grub, the dell bios image, nothing.

---

### Post by Linicks on 2007-10-09
Can you attach an external monitor?  That will prove if the LCD is knackered or the video card, I guess.

What about running the dell diagnostics?  That will report most issues.

Nick

---

