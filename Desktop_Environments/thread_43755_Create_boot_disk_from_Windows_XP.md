---
title: "Create boot disk from Windows XP?"
date: 2005-06-23
forum: Desktop Environments
---

### Post by marXman on 2005-06-23
I've managed to overwrite my Ubuntu boot disk, and currently there is no CD-ROM (or equivalent) installed, so I'm unable to boot from the installation-CD. Is there any way I can create a new boot/emergency-disk? I have access to the file system through Windows.

Already tried several rescue-disks, but they all seem to give me the some weird error.

Anyone?

---

### Post by Lunde on 2005-06-23
[QUOTE=marXman]I've managed to overwrite my Ubuntu boot disk, and currently there is no CD-ROM (or equivalent) installed, so I'm unable to boot from the installation-CD. Is there any way I can create a new boot/emergency-disk? I have access to the file system through Windows.

Already tried several rescue-disks, but they all seem to give me the some weird error.

Anyone?[/QUOTE]
Did you have a grub bootloader? 

Maybe this will help
[http://www.openbg.net/sto/os/xml/grub.html](http://www.openbg.net/sto/os/xml/grub.html)

---

### Post by marXman on 2005-06-24
With the link Lunde gave me, I managed to re-build GRUB to a flobby by concatenating the stage1 and stage2-files from my Ubuntu-installation, as described. 

From there, I restored the GRUB bootloader by following the instructions at [http://www.ubuntuforums.org/showpost.php?p=121355&postcount=5](http://www.ubuntuforums.org/showpost.php?p=121355&postcount=5).

Ubuntu users, you rock.

Mange takk/Thank you very much for the support, Lunde :-)

---

