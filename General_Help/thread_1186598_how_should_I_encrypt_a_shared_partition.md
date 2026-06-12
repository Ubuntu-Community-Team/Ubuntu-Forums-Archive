---
title: "how should I encrypt a shared partition?"
date: 2009-06-13
forum: General Help
---

### Post by Iwilllearn2 on 2009-06-13
I want to create and encrypt a partition that both ubuntu and vista can use.
Is there a better file system than fat32 that both can use, and what FREE program should I use to encrypt the partition with? Thanks in advance for the help, and advice.

---

### Post by michy99 on 2009-06-13
Truecrypt works in both Linux and Windows.

---

### Post by Iwilllearn2 on 2009-06-13
> **michy99 said:**
> Truecrypt works in both Linux and Windows.

Thank you, truecrypt looks like it will work for my needs.

I'm still not sure what file system I should use I know that linux and windows will see fat32, but it sucks, is there anything better?

---

### Post by Scotty Bones on 2009-06-13
> **Iwilllearn2 said:**
> Thank you, truecrypt looks like it will work for my needs.

I'm still not sure what file system I should use I know that linux and windows will see fat32, but it sucks, is there anything better?

Your only other real choice (if you could call it that?), is NTFS.

If you really want to do things the difficult way, there is an ext2/3 driver for windows.

EDIT: I do highly recommend TrueCrypt.  The only issue I have had, is when using flash drives on systems where you don't have admin privileges. The TrueCrypt travler program (the portable version) needs that admin access to load the on-the-fly encryption driver. Other than that, its a beautiful thing.

---

### Post by Iwilllearn2 on 2009-06-13
> **Scotty Bones said:**
> Your only other real choice (if you could call it that?), is NTFS.

If you really want to do things the difficult way, there is an ext2/3 driver for windows.

EDIT: I do highly recommend TrueCrypt.  The only issue I have had, is when using flash drives on systems where you don't have admin privileges. The TrueCrypt travler program (the portable version) needs that admin access to load the on-the-fly encryption driver. Other than that, its a beautiful thing.

Since my main windows partition is NTFS I'll use it, it can't be worse than fat32. I just didn't think linux liked it, but then again if ubuntu doesn't like NTFS how would wubi work?
I have nothing stored on the partition right now so if NTFS doesn't work I can still try something else, and I don't think I'll go the ext2/3 route it just seems like to much hassle.
Thank you for your help!

---

### Post by Iwilllearn2 on 2009-06-13
TrueCrypt reformats the partition for you and only offers NTFS & FAT anyway, so if I was going to use a different format I'd have to use a different program. I thing NTFS will work, if it doesn't I'll just settle with FAT32.

---

### Post by Scotty Bones on 2009-06-14
NTFS will work just fine for you. For all its faults, it is better than using FAT. Ubuntu will handle it just fine. For what it's worth, most of my partitions are NTFS and I've never had any problems.



PS: The whole ext2/3 driver for windows thing was just a joke. I was in one of those moods earlier today.

---

