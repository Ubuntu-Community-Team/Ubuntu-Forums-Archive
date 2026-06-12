---
title: "Dualbooting with Vista"
date: 2009-01-20
forum: General Help
---

### Post by venn on 2009-01-20
And as of now, everything is fine *except* I can't access my Vista partition.

In essence, I just don't know what to edit into menu.lst to make it boot Vista.

There's some thing you put into the terminal that people always ask to have posted that gives HDD information, but I don't know what it is. So if you guys need that, just say so. I did a lot of research and still haven't fixed this, so quick help would be appreciated.

---

### Post by pingpongkid5 on 2009-01-20
I'd say just get rid of any windows os that you have!! :D:D:D:D

---

### Post by venn on 2009-01-20
I'd say that's complete jackass trolling while I'm asking for help.:D:D:D:D:D

---

### Post by venn on 2009-01-20
Wow threads here die fast.

Bumping due to needing to get onto my Vista partition quickly.

---

### Post by venn on 2009-01-20
If repeat posting is frowned upon, just say so.

I'm bumping this back to the first page, very important that I get this fixed ASAP.

---

### Post by Jeff.Smith on 2009-01-20
> **venn said:**
> And as of now, everything is fine *except* I can't access my Vista partition.

In essence, I just don't know what to edit into menu.lst to make it boot Vista.

There's some thing you put into the terminal that people always ask to have posted that gives HDD information, but I don't know what it is. So if you guys need that, just say so. I did a lot of research and still haven't fixed this, so quick help would be appreciated.


I had a similar problem. If you still have the disc you used to install windows vista see if you can run the Memory diagnostics or recovery from it. I'm tried several things that was what ended up working.

There may be a corrupted file that is keeping it from booting. 

Don't know if this will help but it is worth a try.

-Jeff

---

### Post by venn on 2009-01-20
Ironically that was my original plan, just recover the original windows booter.

But I can't, because of needing drivers for my HDD which I still can't find.

So I'm just waiting for someone to come along and tell me what to put into my menu.lst to make Vista boot correctly.

---

### Post by Jeff.Smith on 2009-01-20
You can't boot from the cd drive?

---

### Post by lunatic59 on 2009-01-20
Try adding this to your menu.lst file

[FONT="Courier New"]title Microsoft Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1[/FONT]

Where hd0 is your first [only] hard disk and the second number represents the partition [partitions start at 0] so the above example is to boot from the first partition on the first hard disk.

if you are not sure which is your Vista partition, type:

[FONT="Courier New"]sudo fdisk -l
[/FONT]
You'l see something like this:

[FONT="Courier New"]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3422    27487183+   7  HPFS/NTFS
/dev/sda2            3423        3484      498015   82  Linux swap / Solaris
/dev/sda3            3485       19457   128303122+  83  Linux

[/FONT]
In this example the NTFS partition is indeed the first on the only hard disk.

---

### Post by Gondee on 2009-01-20
Now of course the partition that it is on is going to be different. But this is what i have to boot into vista.

type this in the terminal:
```
sudo gedit /boot/grub/menu.lst
```

Then add this to the end.
**This is assuming its on the first hardrive, on the first partition.**
```


title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```




If thats already in there, post your grub list here.

---

### Post by venn on 2009-01-21
Love you guys. Exactly what I'm looking for.

When I get home (at school now) I'll try it.

Will report results.

---

### Post by venn on 2009-01-21
All's fine now.

You guys did an amazingly quick job fixing it.

Couldn't have asked for better help.

---

