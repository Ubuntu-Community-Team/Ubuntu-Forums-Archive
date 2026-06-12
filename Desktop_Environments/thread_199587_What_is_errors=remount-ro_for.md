---
title: "What is errors=remount-ro for?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by lzap on 2006-06-19
Hello,

I have changed my fstab entry to this:

```
/dev/hda8 / ext3 defaults,errors=remount-ro,noatime,data=writeback 0 1
```

And the system did booted in readonly. I have had to boot the live CD and correct it to default "**defaults,errors=remount-ro**". What was wrong with my setup?

And -- what is **errors=remount-ro** for? Do I need it?

*ps - is there any chance to switch dir_index option on a ext3 filesystem with data (I mean non destructive change)?*

---

### Post by Alpha_Cluster on 2006-06-19
Im pritty sure that the errors command stops the error from being reported.

---

### Post by lzap on 2006-06-19
I have found: ext3 shows an error message like:

Cannot change data option while remount.

Strange thing is I have already added rootflags=data=writeback to the kernel :-(

---

### Post by [S|G] on 2006-06-19
errors=remount-ro will mount the filesystem in read-only mode in case there are any problems with it. This prevents you from potentially losing data using a bad filesystem. 

If this happened to one of your partitions, you should probably boot from a livecd or floppy (if it's not on your root partition, you can boot on recovery mode) and then run fsck on the affected disk.

---

