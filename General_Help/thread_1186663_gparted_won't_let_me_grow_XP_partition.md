---
title: "gparted won't let me grow XP partition"
date: 2009-06-13
forum: General Help
---

### Post by fiddler616 on 2009-06-13
Hello,
I got a new game today, and realized there wasn't enough space on my XP partition to install it. So I dutifully booted up a Live CD, ran "gksu gparted", shrunk down my /home partition, moved things around to make space for the XP partition to grow into--and gparted won't let me grow it. Or move it.
ASCII diagram:

```

|------------------------------------------|
|[Windows XP]|[Unformatted][Swap][/home][/]|
|------------^Unpassable barrier-----------|

```

And I tried just making a new partition, but the game has ideas, and *must* be installed on the C:\ drive. Stupid DRM. This is why proprietary software makes me twitchy.

Everything was unmounted.

What do I do? Thank you.

---

### Post by synapsys on 2009-06-13
Do you have ntfsprogs package installed?

Also always remember to defrag before you resize any windows partition.

---

### Post by merlinus on 2009-06-13
Perhaps format the free space as ntfs?

Also, are you using the gparted cd or the version on ubuntu?

---

### Post by fiddler616 on 2009-06-13
I don't know if I have ntfsprogs installed or not, but one would assume it came on the Live CD, right? And I've done this successfully on a different laptop with Intrepid...

@Merlinus: I did try making a new partition, but the game must be installed on the C:\ drive. See OP for mini-rant about DRM.

I'm using a Jaunty CD with gparted on it, not the gparted CD itself.

---

### Post by trecool999 on 2009-06-13
Make sure you have ntfsprog. I'm pretty sure Ubuntu doesn't have it preinstalled. Mine didn't.

It may take a while, but you might try moving a small amount of the unformatted space in front of XP, then moving it back. Again, depending on the size of your XP partition, making Gparted lug it around could take some serious time.

---

### Post by drs305 on 2009-06-13
Is the free space inside the extended partition (i.e. inside the light blue border)? You can't take free space from inside the extended partition and put it in a primary partition.

If this is the case, you must first shrink the extended partition and then you will be able to add it to the adjacent primary partition.

The latest versions of gparted should be able to handle ntfs partitions - you can check via the main menu: View, File System Support.

If what I describe isn't the case perhaps you can post a pic of the current setup as displayed by gparted.

---

### Post by fiddler616 on 2009-06-13
> **drs305 said:**
> Is the free space inside the extended partition (i.e. inside the light blue border)? You can't take free space from inside the extended partition and put it in a primary partition.

If this is the case, you must first shrink the extended partition and then you will be able to add it to the adjacent primary partition.
I forget the colors, but I shrunk one partition, leaving unformatted space next to XP, and it would grow into it. I also tried shrinking the XP partition, and nothing would move/grow past the line that used to be the end of the partition.

---

### Post by fiddler616 on 2009-06-13
I'm going to boot of the Live CD again to give you guys a screenshot.

---

### Post by fiddler616 on 2009-06-13
Ah, drs305 wins. The free space was indeed in an extended partition.

*Solved* (Although doing anything with gparted makes me nervous...hopefully I'm not back in a new thread complaining about GRUB Error 17 or 22...)

Thanks, everyone!

---

