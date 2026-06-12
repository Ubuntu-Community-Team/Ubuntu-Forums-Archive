---
title: "rsync to move OS from hda4 to hda1"
date: 2010-03-04
forum: Desktop Environments
---

### Post by Barriehie on 2010-03-04
Hey all,
Anyone see any issues with this? /home is on another drive and I'll be booting from a liveCD before doing this.  After the below command I'll just have to edit menu.lst and fstab.

```

rsync -avrpl --exclude "home/*" --exclude "dev/*" --exclude "sys/*" --exclude "proc/*" ./media/hda4  ./media/hda1
```

TIA,
Barrie

---

### Post by Fire_Chief on 2010-03-04
You don't have to include the -rpl switches when using -a as that is implied. Other than that it looks ok.

You could fire up GParted from the liveCD (or get the GParted standalone liveCD) and perform a full partition copy at the block level instead of the file level. This should be faster and less tedious plus you have the option to expand the new partition to fill the drive space (if target drive is larger).

Cheers!

---

### Post by Barriehie on 2010-03-04
> **Fire_Chief said:**
> You don't have to include the -rpl switches when using -a as that is implied. Other than that it looks ok.

You could fire up GParted from the liveCD (or get the GParted standalone liveCD) and perform a full partition copy at the block level instead of the file level. This should be faster and less tedious plus you have the option to expand the new partition to fill the drive space (if target drive is larger).

Cheers!

Thank you for the prompt reply Fire_Chief.  I've got the GParted liveCD but as yet can't remember if it will let me get to a terminal to edit the menu.lst and fstab files.  I'll post back upon completion, as yet haven't found much info on doing this on the net.

Edit: If I do this at the block level will it wreck the boot sector???  I don't want to have to mess around with making the machine boot!  (although I've got the supergrub boot cd...)

---

### Post by Fire_Chief on 2010-03-05
You'll still need to re-run grub on the new drive after you get the menu.lst file corrected so it will know how to reach the drive. If the old drive is not going to stay in the computer, I would wait to setup grub until you've removed the old HDD. That way you won't have to change grub twice.

Essentially the MBR on the new drive doesn't know about the Ubuntu install you just copied to it (this is the same regardless of copy method). So wherever you keep your MBR for the system to reach GRUB, it will need to be told how to find the new drive. This may be fairly automatic via grub-install...but I'm a bit rusty on that part.

Cheers!

---

### Post by Barriehie on 2010-03-05
> **Fire_Chief said:**
> You'll still need to re-run grub on the new drive after you get the menu.lst file corrected so it will know how to reach the drive. If the old drive is not going to stay in the computer, I would wait to setup grub until you've removed the old HDD. That way you won't have to change grub twice.

Essentially the MBR on the new drive doesn't know about the Ubuntu install you just copied to it (this is the same regardless of copy method). So wherever you keep your MBR for the system to reach GRUB, it will need to be told how to find the new drive. This may be fairly automatic via grub-install...but I'm a bit rusty on that part.

Cheers!

No new drives, I'm just moving Debian from hda4 to hda1 on the same drive, the one I'm currently booting from.  So, I should be able to rm -** the files/folders on hda1, copy hda4 to hda1, edit menu.lst and fstab and then reboot.

Barrie

---

### Post by Barriehie on 2010-03-06
Not to drink so much coffee next time!  So I mounted hda1 and removed all folders/files and then rsync'ed from hda4 > hda1 and rebooted with the super grup CD.  This then made the grub install on hda4 match the OS copied onto hda1.  Rebooted and in gparted formatted hda4 and then booted again with the super grub CD.  It then updated the grub install on hda1 to match that as being the only bootable partition and all is well!!!

Thanks for your help Fire_Chief.

Barrie

---

