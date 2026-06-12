---
title: "Changing desktop resolution"
date: 2009-12-17
forum: Desktop Environments
---

### Post by CuboDeAgua on 2009-12-17
Hi all. I'm a linux newbie.

I've just installed Ubuntu 9.10 in my old computer. It has one S3 Virge as graphics board.

The problem is that i can't set the resolution to 1028x768 because it's not available.
Before, i had a windows xp installed here an the working resolution was 1028x768.

I think the S3 virge drivers are properly installed.
I've read some posts around the internet and all of them talk about xorg.conf file modifications, but the problem is that i haven't that file in my computer (as far as i can say). I've tried creating one through many commands and solved some of the problems that those commands dropped, but i've always finished in a dead end.

Can anybody tell me any hints?

Thanks in advance ^^

I've already tried the following:
$ sudo dpkg-reconfigure xserver-xorg
but no new xorg.conf file created.

Then i created a xorg.conf file myself retrieving the device data from:

lspci | grep -i vga

which was : S3 Inc. 86c325 [ViRGE] (rev 06)

So my xorg.conf file was:

```
Section "Screen"
   Identifier   "Default Screen"
   Device       "S3 Inc. 86c325 [ViRGE] (rev 06)"
   Monitor      "Configured Monitor"
   DefaultDepth   24
   SubSection "Display"
      Depth      1
      Modes      "1280x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      4
      Modes      "1280x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      8
      Modes      "1280x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      15
      Modes      "1280x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      16
      Modes      "1280x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      24
      Modes      "1280x800" "1024x768" "800x600" "640x480"
   EndSubSection
EndSection
```

But nothing happened and still other resolution options no available.

---

### Post by CuboDeAgua on 2009-12-17
Well, the thing is solved.

The problem was with the defaultdepth parameter.

24 value was too big for my card memory, so setting it to 16 made the 1024-768 resolution option apear ^^.

---

