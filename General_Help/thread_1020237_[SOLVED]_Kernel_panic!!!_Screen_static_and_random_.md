---
title: "[SOLVED] Kernel panic!!! Screen static and random dots!? HELP!"
date: 2008-12-23
forum: General Help
---

### Post by linuxisevolution on 2008-12-23
Well.... I was trying to recover some files off of a 2.5" hdd with a cable adapter. I plugged the IDE cable in the adapter, and **blue and puple lines** filled the xubuntu taskbar and **the mouse would not move**. Upon reboot, I am prompted with "Kernel panic -not syncing: Attempted to kill the idle task!" And static on the screen.

I'll take a picture and post it once I find my camera. 




Any thoughts to what's wrong?

:confused:

Thanks. :(

---

### Post by linuxisevolution on 2008-12-23
> **linuxisevolution said:**
> Well.... I was trying to recover some files off of a 2.5" hdd with a cable adapter. I plugged the IDE cable in the adapter, and **blue and puple lines** filled the xubuntu taskbar and **the mouse would not move**. Upon reboot, I am prompted with "Kernel panic -not syncing: Attempted to kill the idle task!" And static on the screen.

I'll take a picture and post it once I find my camera. 




Any thoughts to what's wrong?

:confused:

Thanks. :(


SOLVED!  I removed the last memory chip. She now has 348mb ram and not 512mb, but it's not like you could do much with 8mb max video memory anyway.. :lolflag: I guess the ide harddrive was bad and cause the psu to go biserk which caused a spike that ruined a stick of memory? Just my luck...

---

### Post by Titan8990 on 2008-12-23
IDE drives are not "hot-swappable"....


Edit: You should always turn your PC off when adding or removing non-plug and play devices.

---

### Post by linuxisevolution on 2008-12-23
> **Titan8990 said:**
> IDE drives are not "hot-swappable"....

Yeah, now I know that. I figured they were because I could remove the drives and replace them in my server while it is running, and they are ide. Thanks for the support. . . . . .



EDIT: Video finnished uploading. For those seeking help, this is what happened:

[Video]("http://s289.photobucket.com/albums/ll207/winrid/?action=view&current=SANY0215.flv")

---

