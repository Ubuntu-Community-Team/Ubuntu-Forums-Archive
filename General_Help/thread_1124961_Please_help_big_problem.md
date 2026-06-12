---
title: "Please help: big problem"
date: 2009-04-13
forum: General Help
---

### Post by Asbian on 2009-04-13
I have recently been trying to convert from Windows XP to Ubuntu. I ordered the free disc from ubuntu.com just to ensure I didn't make any mistakes. I just loaded it up into my computer, and selected the second option: "Install on top of windows" or something like that. I got the idea that this was WUBI. Now when I turn my computer on, it shows the dell screen where I can enter BIOS like usualy, then goes to the screen where it says "Initializing Intel(R) Boot Agent... etc.", but this is what the page fully says now:

```

Initializing Intel(R) Boot Agent Version 3.0.03
PXE 2.0 Build 078 (WfM 2.0), RPL V2.73


Intel(R) Boot Agent Version 3.0.03
Copyright (C) 1997-2000, Intel Corporation
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.

SYSLINUX 3.72 2008-09-25 EBIOS Copyright (C) 1994-2008 H. Peter Anvin
Could not find kernel image: linux
boot:_

```

the underscore after "boot:" expects me to type something, but I don't know what. The media test failure thing means nothing to me, because I always get it. Someone please help.

---

### Post by 3Miro on 2009-04-13
This isn't good. Wibi is initialized form within windows. Right now XP is probably dead.

Now is it doing this, I don't exactly know. Try booting from the LiveCD, but instead of selecting Install, on the very first menu select "Try without changes". That will boot Linux and will give you a chance to see what happened.

Someone more knowledgable than me would have to take you from there. You can see if there is still a NTFS windows partition present. Recovering anything or fixing GRUB (the boot loader) is somewhat beyond me.

(with the LiveCD you would at leas be able to use you computer for Internet)

---

### Post by Asbian on 2009-04-14
When I try to liveboot, the screen goes beige and I can see & move the cursor but the desktop never loads. I INSTALLED IT ON MY HARD DRIVE; NOT MY FLASH DRIVE!

---

### Post by lindsay7 on 2009-04-14
From what I read, you do not want windows anyway and your disk drive is a mess at this time. I would download Gparted and burn it to a cd or dvd (read the instructions on their web site, it will be a live cd which means that it will boot up when installed in you computer at start up). Format your drive using Gparted, I would format it as ext3 file system. Once this is done you should be able to install Ubuntu from the live cd. Use the guided option (it should be the easies).

---

