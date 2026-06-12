---
title: "Routine Disk Check Fails"
date: 2009-06-20
forum: General Help
---

### Post by Bubblebeard on 2009-06-20
Hi,

I recently upgraded from vista to ubuntu, however the routine disk checks on startup have failed in ubuntu.  It has done two checks so far; both failed at 1%.

After failing, it prompts me to enter fsck manually and sets up a terminal as root.  I type fsck, and it goes through a long process involving a lot of
> [262.224428] Buffer I/O error on device sda1, logical block 6324255
Error reading block 6324255 Attempt to read block from filesystem resulted in a short read) while getting next inode from scan. Ignore error<y>? yes
Force rewrite<y>? yes

sequences (the numbers progess as the scan goes on and not all of them fail).  If I type no instead at the ignore error or force rewrite prompts, it fails and I need to start over.  So I enter my yeses and it eventually finishes, saying > /dev/sda1: 211305/14647296 files (0.6% non-contiguous), 5581488/58564949 blocks

I then press Control-D as it told me to restart the computer and the computer restarted fine and works normally.  Does anyone know what the problem is or how to fix it? 

Thanks!

---

### Post by thewolfman on 2009-06-20
I had a similar problem recently and to save yourself a lot of headache I would completely re-format (at least) your root (/) partition.

My drive wasn't formatted correctly (never found out why) and like I said, I re-installed my root partition it it runs like clockwork since.

Seriously to save a lot of hassle, just do what I suggest because the errors messages won't go away!.

Have a good one

---

### Post by philinux on 2009-06-20
Boot it again and when it tells you run fsck manually do it like this.

```
fsck -v
```

This means verbose mode. It it offers to fix any problems hit the y key.

Good luck it should fix it.

---

### Post by Bubblebeard on 2009-06-20
> **philinux said:**
> Boot it again and when it tells you run fsck manually do it like this.

```
fsck -v
```

This means verbose mode. It it offers to fix any problems hit the y key.

Good luck it should fix it.

Ok... for now I already did regular fsck, but I could do fsck -v next time I guess... Is there a way to do this before the next time my computer fails one of these automatic checks?  I don't know how to start a maintenance shell.

It would be nice if this worked so I do not have to reformat my drive.

Thanks for the help!

---

### Post by philinux on 2009-06-20
> **Bubblebeard said:**
> Ok... for now I already did regular fsck, but I could do fsck -v next time I guess... Is there a way to do this before the next time my computer fails one of these automatic checks?  I don't know how to start a maintenance shell.

It would be nice if this worked so I do not have to reformat my drive.

Thanks for the help!

Press esc as soon as grub appears then use the down arrow to select recovery mode.

---

