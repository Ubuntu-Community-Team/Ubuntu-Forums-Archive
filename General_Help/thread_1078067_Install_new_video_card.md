---
title: "Install new video card"
date: 2009-02-22
forum: General Help
---

### Post by pan69 on 2009-02-22
Hi all,

I currently have an old ATI video card that is giving me grief (I think it's because of the drivers). I heard good stuff about NVidia boards and the drivers that come with it.

I was wondering, what would be the best way to switch video cards? Can I just rip out the old one and put in the new one? Maybe it would be better to disable the current drivers and switch to generic VESA mode and uninstall the old drivers before doing this? If so, what are the best steps involved?

Thanks
Luke

PS: I'm running Intrepid/Gnome/ATI.

---

### Post by dcstar on 2009-02-23
> **pan69 said:**
> Hi all,

I currently have an old ATI video card that is giving me grief (I think it's because of the drivers). I heard good stuff about NVidia boards and the drivers that come with it.

I was wondering, what would be the best way to switch video cards? Can I just rip out the old one and put in the new one? Maybe it would be better to disable the current drivers and switch to generic VESA mode and uninstall the old drivers before doing this? If so, what are the best steps involved?

Thanks
Luke

PS: I'm running Intrepid/Gnome/ATI.

You are on the right track, most video is autodetected at boot these days and as long as your xorg.conf is set to use the autodetected stuff you should be pretty right.

---

### Post by blazemore on 2009-02-23
1. Uninstall the ATI driver
2. Download the Nvidia driver setup, save it in your home directory
3. Turn off your pc, install the new card
4. Boot up. If you can't get X to run, you can install the Nvidia driver you downloaded, using the command line.

X will probably work though. You'll have to install the nVidia driver, 180 is very good now.

---

