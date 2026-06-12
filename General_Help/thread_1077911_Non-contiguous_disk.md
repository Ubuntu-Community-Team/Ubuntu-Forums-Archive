---
title: "Non-contiguous disk?"
date: 2009-02-22
forum: General Help
---

### Post by djbushido on 2009-02-22
When I go to boot my Xubuntu distro off of a 250Gb usb drive, every time lately it keeps remounting read only as according to fstab. This causes problems with X.org and GDM because my authorization file then can't be **written**. I know Linux is supposed to fragment, but every time I see the fsck results, it says that part of the disk is non-contiguous. Is there a way around this other than removing errors=remount-ro from fstab?

---

### Post by kidders on 2009-02-24
Hi there,

If your root filesystem has errors on it and is mounting in read-only mode, removing "errors=remount-ro" from its mount options will probably make your system unbootable. I suggest taking a look at your dmesg logs for clues about the problem, and going from there. It may, for example, be hardware-related.

**Edit:** Incidentally, all filesystems fragment slightly over time ... it won't cause any issues, aside from a gradually increasing performance penalty. Fragmentation would have to be _extremely_ severe to cause errors.

---

### Post by djbushido on 2009-02-24
Okay, the problem is fixed next time I boot again (fsck running on boot-up - modifying a read-only system is a bad idea indeed), but after shutting down, there is usually a 50-50 chance that I can't boot correctly next time. Dmesg is a good idea, didn't think of that. Anybody have ideas on how to fix this or defrag the disk?

---

### Post by kidders on 2009-02-24
> **djbushido said:**
> Anybody have ideas on how to fix this or defrag the disk?It'd be a very bad idea to defragment your filesystem until you're happy the errors you're seeing have gone away. How fragmented is it?

Also, I wonder if your filesystems are unmounting cleanly when you shut down.

---

### Post by djbushido on 2009-02-25
I didn't _really_ think that it was the disk defragmenting. I don't know how fragmented it is. I don't know how I'd know.

It could very well be the unclean shutdown. How do I check against that, and make sure it doesn't happen again?

---

### Post by vanadium on 2009-02-25
You can force a fsck on the next reboot with the following command

```

sudo touch /forcefsck

```
[edit]Should read "forcefsck" rather than "fsck" [/edit]
If the check does succeed, but you keep getting the error regularly, it might be a hardware issue.

Fragmentation cannot be the cause of your issue.

---

### Post by djbushido on 2009-02-25
I'm pretty sure it's not a fragment problem. I don't know how to check against the unclean shutdown. Is the touch command temporary? If so, I would prefer a way to automatically check every time, rather than just once.

---

### Post by vanadium on 2009-02-26
Your ext3 file systems undergo a quick check using the file system's journal on every start. Only every other day (configurable) an in-depth check is performed. The "sudo touch /forcefsck" command forces a one-time full check on the next reboot.

By the way, please note that I provided the wrong command in my previous post (I corrected it there). To correct, run the command

```

sudo rm /fsck

```

then run the correct command instead:

```

sudo touch /forcefsck

```
Next time you reboot, the drive will be checked, and you will know why you don't want to do this at every boot ;)

Again, if the problem regularly returns, then suspect a hardware problem.

---

### Post by djbushido on 2009-02-26
I already don't want to do this. The problem is that when I don't I don't know when I boot up whether or not the disk will be mounted ro. So when that happens, I have to reboot and then do the check.

I already suspect a hardware issue, as this is fairly consistent. I don't know what hardware issue it is, but like kidders said, I believe it is an unclean shutdown. I don't know how to protect against this or fix it, or whatever, but would really like this to fix itself. I am currently using a Fedora distro (dual-boot) and can use this as well to try and fix it.

---

### Post by vanadium on 2009-02-27
> I don't know what hardware issue it is, but like kidders said, I believe it is an unclean shutdown. I don't know how to protect against this or fix it, or whatever, but would really like this to fix itself
That is not how you solve a hardware issue. To solve a hardware issue, you either repair or replace the hardware, that's all.

---

### Post by djbushido on 2009-02-27
I know what you meant by hardware issue. Sorry. In the mean time, does anybody know what an "unclean" shutdown is and how to fix it?

---

### Post by vanadium on 2009-02-27
Might be, but your answer suggested differently to me.

An unclean shutdown is when the system goes down inproperly without performing all shutdown procedures (e.g. following a power outage or just disconnecting the electricity). For drives, this can mean that not all the data from the memory cache is written, leaving the file system in an inconsistent state.

In fact, an unclean shutdown mostly affects the file systems only (perhaps it also could break hardware?). You recover by checking and eventually repairing the file systems using file checking tools. That will bring the file systems again in a consistent state.

---

### Post by djbushido on 2009-02-27
Okay. Fair enough. Moving on.

I understand now what the unclean shutdown is, but I don't know how to make sure that it does not happen. I think since I am using a USB hard drive that the shutdown write speed is getting affected (can't write fast enough so shutdown occurs before data gets finished writing). In any case, how can I try and make sure that the "unclean shutdown" doesn't happen?

---

