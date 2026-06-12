---
title: "windows xp keeps erasing grub on the mbr"
date: 2005-07-28
forum: Desktop Environments
---

### Post by hardawayd on 2005-07-28
I have xp installed on my first disk and linux on my second disk on my laptop. It appears that when after i launch windows xp from grub and later logout that upon reboot grub is gone.  I have to do a rescue and reinstall grub.  Is there some program in xp that automatically overwrites the mbr?

---

### Post by gmz on 2005-07-28
Is it possible that you have some sort of MBR protection flag set in your BIOS? I've had problems with Grub but have never heard of it getting erased with each load.

---

### Post by blu.gecko on 2005-07-28
I had a similar issue once, I saved grub or lilo to floppy, and set bios to floppy/hda/cdrom on the boot order, If I didnt do floppy xp would start as normal.

might think about doing that, my wife cant even touch my linux anymore.

 \\:D/

---

### Post by drogoh on 2005-07-28
[QUOTE=hardawayd]I have xp installed on my first disk and linux on my second disk on my laptop. It appears that when after i launch windows xp from grub and later logout that upon reboot grub is gone.  I have to do a rescue and reinstall grub.  Is there some program in xp that automatically overwrites the mbr?[/QUOTE]

Windows overwrites your MBR because you installed grub on the Windows MBR I'm assuming.  You can't have it that way; that nice corporation over in Redmond said so.  Now you can get around that by doing a little switch-a-roo on it and tricking Windows into thinking it's still master.  Switch your Linux and Windows drives out so that Linux is primary and install grub on that MBR, reconfiguring grub to your taste.  This is but one in a myriad of solutions.

---

