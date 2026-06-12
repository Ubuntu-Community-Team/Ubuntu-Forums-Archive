---
title: "Grub won't load after windows installation"
date: 2006-08-03
forum: Desktop Environments
---

### Post by ex00r on 2006-08-03
Hi there!

I'm quiet in a mess...

I have Ubuntu Dapper running. all is working. It's on my second HD (hdb). I thought i could install windows XP again after one year not using it. That's what i did. I installed it on the first HD (hda). But now, if i want to start the hdb it says "invalide" something and if i start hda only windows XP loads.

How can i reinstall GRUB to start up with a windows entry? Importent is that grub loads before windows.

thanks people!

---

### Post by ex00r on 2006-08-03
holy shut! Sorry m8ts. I just missed this thread: [http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+windows+installation](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+windows+installation)

I'll give it a try. It's exactely the problem i have.

---

### Post by dewey on 2006-08-04
What happened is Windows installed its own bootloader into the MBR, overtop of GRUB.  All you need to do is use a linux live-cd, and reinstall grub to the MBR, or you can create a GRUB bootdisk onto a cd, usb drive, or floppy.

The link mentioned in the previous post looks like it has very good instructions on reinstalling grub to the MBR.

---

