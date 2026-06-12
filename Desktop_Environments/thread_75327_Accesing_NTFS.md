---
title: "Accesing NTFS"
date: 2005-10-13
forum: Desktop Environments
---

### Post by MuRRe on 2005-10-13
I have a 60 GB data partiation (NTFS).
I can't acces it, it say:
"You do not have permission necessary
to view the contents of "hda5""

please help!!??

---

### Post by bored2k on 2005-10-13
Check with this guide: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by MuRRe on 2005-10-13
Didnt work. its still a cross over the icon.

---

### Post by piggyaugu on 2005-10-13
[QUOTE=MuRRe]I have a 60 GB data partiation (NTFS).
I can't acces it, it say:
"You do not have permission necessary
to view the contents of "hda5""

please help!!??[/QUOTE]


mannually you can do this:

mount /dev/hdaX /XXXXX **-o umask=0**

this will allow all users get access to the partition

or you can edit your fstab to make it automatic

---

### Post by aysiu on 2005-10-13
Try rebooting.
Also, realize that the instructions are for /dev/hda1, but you said you're using /dev/hda5--make sure you change that.

---

### Post by NXArmada on 2005-10-13
They need to add more support for NTFS volume so that we can Read and Write to them.  Mandriva Linux can read and write to NTFS, ubuntu should too.

---

### Post by T-One on 2005-10-13
[QUOTE=NXArmada]They need to add more support for NTFS volume so that we can Read and Write to them.  Mandriva Linux can read and write to NTFS, ubuntu should too.[/QUOTE]

I thought NTFS Read was widely supported, while Write is still experimental and can cause some corruption to the partitions?

Somebody correct me, as I would GREATLY benefit from NTFS write, but figured it was unsafe...

---

### Post by NXArmada on 2005-10-13
before i found Ubuntu (Best Distro), i was useing Mandriva Linux (Mandrake Linux) and it had full support for NTFS and i had no problems with it in Windows or Linux.  So i was wondering if the ubuntu team can find out how they did that and use it.  I still perfer Ubuntu over Mandriva despate the NTFS problems i can read my NTFS and thats good for now.

---

### Post by drogoh on 2005-10-13
[QUOTE=NXArmada]before i found Ubuntu (Best Distro), i was useing Mandriva Linux (Mandrake Linux) and it had full support for NTFS and i had no problems with it in Windows or Linux.  So i was wondering if the ubuntu team can find out how they did that and use it.  I still perfer Ubuntu over Mandriva despate the NTFS problems i can read my NTFS and thats good for now.[/QUOTE]

The fact of the matter is that NTFS writing is dangerous and can cause the world to end if you're not careful.  Just because N distro chooses to enable it doesn't mean it won't seriously screw your data up.  I doubt they made any changes to the NTFS code at all, just enabled a potentially dangerous kernel option that is and most probably always will be experimental.

You're free to compile your own kernel with NTFS write enabled but do be aware of the risks before doing such.

But this is getting off topic.... I hope MuRRe was able to successfully access their NTFS data.

---

### Post by Unit #134679 on 2005-10-13
[QUOTE=drogoh]The fact of the matter is that NTFS writing is dangerous and can cause the world to end if you're not careful.  Just because N distro chooses to enable it doesn't mean it won't seriously screw your data up.  I doubt they made any changes to the NTFS code at all, just enabled a potentially dangerous kernel option that is and most probably always will be experimental.

You're free to compile your own kernel with NTFS write enabled but do be aware of the risks before doing such.

But this is getting off topic.... I hope MuRRe was able to successfully access their NTFS data.[/QUOTE]

You can use the guide in the Ubuntu FAQ Guide (System>Help>Ubuntu 5.10 Starter Guide>Windows Partitions) to set it up. Its pretty much like the UbuntuGuide.

---

### Post by Karasu Tengu on 2005-10-13
Simply umount it, 
then set the permissions on the mount file
set the options in the fstab
remount then your good to go

write your fstab in here if you still have problems

---

### Post by Antman on 2005-10-13
[QUOTE=NXArmada]before i found Ubuntu (Best Distro), i was useing Mandriva Linux (Mandrake Linux) and it had full support for NTFS and i had no problems with it in Windows or Linux.  So i was wondering if the ubuntu team can find out how they did that and use it.  I still perfer Ubuntu over Mandriva despate the NTFS problems i can read my NTFS and thats good for now.[/QUOTE]

Mandriva does **NOT** have this enabled by default. Someone must have tweaked your configuration.

Ant

---

