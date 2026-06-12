---
title: "Dosbox broken in Hardy"
date: 2009-06-26
forum: Gaming &amp; Leisure
---

### Post by afrodeity on 2009-06-26
Gosh this is irritating.

```

afrodeity@afrodeity-desktop:~$ dosbox
dosbox: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS32
afrodeity@afrodeity-desktop:~$ 

```

WHat is going on, how is this possible? The elves are doing something strange?

---

### Post by CharmyBee on 2009-06-26
Not a stock dosbox.conf probably. Try output=surface.

---

### Post by FrozenFox on 2009-06-26
EDIT: Upon looking around at packages.ubuntu.com, it seems libgl.so.1 is provided by nvidia-glx. You should probably wait for advice from someone who would know better as far as ubuntu goes before you try it, but I think having the 32 bit version of that would solve your issue..

EDIT2: [http://ubuntuforums.org/showthread.php?t=481740](http://ubuntuforums.org/showthread.php?t=481740) perhaps that post might help you. See cappy's response.

You might want to file a bug report if that's from an official package.

Elf class errors of the sort in my experience pretty much always result from being on a 64 bit system trying to use a 32 bit program without the needed 32 bit libraries. Or vice versa on occasion, if you really managed to screw up ;) . 

Libgl.so is provided by the video drivers, I believe. On the assumption you're using an nvidia card, see if you can install the 32 bit version of nvidia-utils (not sure if on ubuntu it's separate from the nvidia driver package itself). I'm not on ubuntu anymore, so I couldn't tell you precisely where to get that stuff or what it's called, but that's most likely what you need. (EDIT: See edits above ;P )

---

### Post by afrodeity on 2009-06-26
Its a problem which affects the [Via Chrome 9 driver for the P4M900 chipset ]("http://www.tkarena.com/forums/linux-arena/39476-help-editing-xorg-p4m900-linux-graphics-driver-ubuntu-8-04-a.html?=#post245582")which doesn't appear to support 64bit and comes up with an ELF class error. I dropped back to the previous xorg.conf and didn't uninstall with the script they provide, so the problem might rectify if I do this. Will keep you posted.

---

### Post by afrodeity on 2009-06-28
As I suspected. I uninstalled the VIA driver and DOSbox is now working. But this could also be because the Openchrome drivers were installed automatically, and my installing another driver, albeit a native VIA driver introduces some form of conflict? Wish there was an expert around, because Openchrome has a lot of dependencies and was installed when I installed from original Ubuntu Disk, in which case the VIA installer script should take this into account?

---

