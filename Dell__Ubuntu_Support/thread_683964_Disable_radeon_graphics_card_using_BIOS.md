---
title: "Disable radeon graphics card using BIOS?"
date: 2008-01-31
forum: Dell  Ubuntu Support
---

### Post by nosushi4you on 2008-01-31
I have a DELL 4600 computer, with an ATI Radeon 7000 graphics card and an Intel graphics card. Ubuntu will not load using my ATI card, so I want to disable the card through my BIOS. How would I go about doing this?

---

### Post by nosushi4you on 2008-01-31
Alright, so I looked on my BIOS, and there are two options for graphics controllers: AUTO and INTEGRATED. I'm guessing the INTEGRATED card would be my Intel, so should I switch it to that. It is currently set to auto.

---

### Post by neptho on 2008-02-01
If you wish to use the internal (likely i810) video, it would be much easier to just remove the ATI card; this will free up system resources, and the machine will automatically use the internal video.

However, you do want to set the option to the 'Internal' card.  If it gives you the option in the BIOS, ensure you give it at least 4MB of RAM.

"Integrated" may, or may not disable the ATI card; but I can not imagine why the 7000 would not work.  It's old, but it's a very, very common card and worked fine in XF86 v3/4.  Have you tried to do an 'apt-get install  xserver-xorg-video-ati' if the installer does not load into a GUI, then '/etc/init.d/gpm restart' ?

---

