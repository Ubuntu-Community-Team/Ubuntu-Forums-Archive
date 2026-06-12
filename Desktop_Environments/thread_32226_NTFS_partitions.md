---
title: "NTFS partitions"
date: 2005-05-06
forum: Desktop Environments
---

### Post by jonnybourse on 2005-05-06
I need to continue to run XP on a dual boot machine. I have two hard drives and successfully use suse as my preferred linux os alongside XP. Can ubuntu read the NTFS partitions as suse can? It appeared as though that was not possible on the otherwise delightful ubuntu live cd running gnome.

TIA yours jonny

---

### Post by 23meg on 2005-05-06
yes it can, no doubts. check out ubuntuguide.org for help on how to mount them.

---

### Post by kosmic on 2005-05-06
Yes you can, the only drawback is that you have to manualy mount them in fstab.

if you need help please read the Ubuntu Guide, or press the help buton in the ubuntu distro (in gnome)

---

### Post by kvidell on 2005-05-06
[QUOTE=jonnybourse]I need to continue to run XP on a dual boot machine. I have two hard drives and successfully use suse as my preferred linux os alongside XP. Can ubuntu read the NTFS partitions as suse can? It appeared as though that was not possible on the otherwise delightful ubuntu live cd running gnome.

TIA yours jonny[/QUOTE]
 If you install the NTFS module (if the actual install doesn't come with it, I'm unsure. Mine appears to have but I'm running Breezy).
modprobe ntfs
mount -t ntfs /dev/ntfsdrivename /place/to/put/it
Should work just fine.
- Kev

---

### Post by lorap on 2005-05-06
hi friend!
yes you can,moreover you'll find soon out ubuntu's as good as suse.
but i preffer ubuntu:-)
try running it and you'll understand why.

---

### Post by davidmigl on 2005-05-07
[QUOTE=kosmic]Yes you can, the only drawback is that you have to manualy mount them in fstab.

if you need help please read the Ubuntu Guide, or press the help buton in the ubuntu distro (in gnome)[/QUOTE]
 Nice.  Is there any way to read Ubuntu partitions in Windows?  While I'm at it, what file system does Ubuntu use anyway?

---

### Post by calvinpriest on 2005-05-07
By default Ubuntu uses ext3 partitions.  Another popular *nix partition type is Reiser, although there are actually several more including XFS...

---

### Post by Buffalo Soldier on 2005-05-07
[QUOTE=jonnybourse]Can ubuntu read the NTFS partitions as suse can?[/QUOTE][http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by maruchan on 2005-05-07
> Nice. Is there any way to read Ubuntu partitions in Windows?

I do this all the time. Use Explore2FS (a Windows app).

---

