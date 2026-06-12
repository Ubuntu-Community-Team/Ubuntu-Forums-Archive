---
title: "[SOLVED] Creating a partition"
date: 2008-12-10
forum: General Help
---

### Post by Dumbestcrayon on 2008-12-10
I have Gnome Partition Editor and I recently switched back to Ubuntu from the waste of time we all call Windows. I had a NTFS partition that I kept all of my stuff on and I am able to use it okay but I have noticed some things that I don't like... Either way that's besides the point. 

I'm going to delete this partition and create a new one for all of my stuff.
What kind of partition should I make it if I'm only using Ubuntu? I don't think I should do NTFS but I don't know what to make it.

---

### Post by adult swim on 2008-12-10
if you are only going to use it with ubuntu then EXT3 would probably be your best bet.

---

### Post by cdtech on 2008-12-10
Also be aware that when formating to NTFS (using gparted) if you decide to install Windows Vista, Vista will not detect the partition for some reason. Using FAT32 is best for sharing between Windows and GNU/Linux. By using FAT32 if at some point you want to connect an external drive (Windows), you can share both using FAT32.

Just my two cents......

---

### Post by Rocket2DMn on 2008-12-10
+1 for ext3, it is a native filesystem with journaling, and has *nix permissions (rwx and ownership).  FAT32 is also recognized out of the box, but doesn't have permissions the same way ext3 does, thought is is recognized by Windows.

---

