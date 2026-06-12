---
title: "Desktop mounting of partition..."
date: 2005-12-20
forum: General Help
---

### Post by theb on 2005-12-20
Hi,

New user here and so far so good.  

I installed ubuntu on my toshiba libretto u105 with four partitions.  One for XP(NTFS), ubuntu (ext3), swap, and one for storage (fat32).  I see all my partitions and everything works so far.  My question is, my 'storage' partition is located in my file system but I want it to mount on my desktop like my XP (hda1).  I don't want a shortcut to it, I guess I can do that but I'd like to know how to mount it on my desktop instead. 

right now, my drives are mounted like so:

hda1 (XP) /dev/hda1 mounted on /
hda2 (ubuntu) /dev/hda2 mounted on /media/hda1
hda6 (storage) /dev/hda6 mounted on /storage

Hope someone can help me...

---

### Post by BathroomNinja on 2005-12-20
I'm a bit confused.  by 'mount it on my desktop', do you mean that you want the icon for the drive on your desktop for easy access, or that you want your /home directory to BE the fat32 drive?

---

### Post by theb on 2005-12-20
[QUOTE=BathroomNinja]I'm a bit confused.  by 'mount it on my desktop', do you mean that you want the icon for the drive on your desktop for easy access, or that you want your /home directory to BE the fat32 drive?[/QUOTE]


sorry for not being clear.  I just want the icon to be on my desktop for easy access.

---

### Post by BathroomNinja on 2005-12-21
basically, you need to edit your /etc/fstab
User aysiu has a really great guide here: [http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

I use this to mount 3 partitions at boot.

Please note however, that I *really* don't think you want to mount a windows partition to /
That would overwrite your linux root folder.  I high recomend something more along the lines of mounting them to /media/Cshared  or /media/Ddrive or what not.  Creating a folder in /media for them helps you to remember what they are and keep them in a nice and neat place.

Having them auto mount by placing them in the fstab, will give you icons for them on the desktop.

---

