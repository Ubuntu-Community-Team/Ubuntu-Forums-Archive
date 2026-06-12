---
title: "Floppy disks unsupported?"
date: 2009-02-07
forum: General Help
---

### Post by Milambar on 2009-02-07
Ok, I have been given an old PC without a hard disk (this will be fixed soon), but it still runs, because I can boot off the Intrepid Ibex CD, and use it as a Live CD.

The system comes with a Floppy Drive (remember those?), and I need to copy some files onto a floppy disk, to create a bios flash disk.

I have an msdos floppy disk, with space for the flash utility. I have the flash utility on a USB stick... But I cannot copy the utility over to the floppy. Why? Because Ubuntu doesn't seem to even recognise the floppy drive at all.

Now.. The floppy drive works, as does the disk as I can boot msdos from it by booting without the Ibex CD in the drive. So theres not a hardware problem, or a problem with the disk itself.

So, how can I fix this?

---

### Post by RHTopics on 2009-02-07
You are right the floppy drive is not supported out of the box in 8.10.

Here is a link describing how to solve this problem:

[http://ubuntuforums.org/showthread.php?t=1014347&highlight=mount+floppy](http://ubuntuforums.org/showthread.php?t=1014347&highlight=mount+floppy)

---

### Post by dcstar on 2009-02-07
> **Milambar said:**
> Ok, I have been given an old PC without a hard disk (this will be fixed soon), but it still runs, because I can boot off the Intrepid Ibex CD, and use it as a Live CD.

The system comes with a Floppy Drive (remember those?), and I need to copy some files onto a floppy disk, to create a bios flash disk.

I have an msdos floppy disk, with space for the flash utility. I have the flash utility on a USB stick... But I cannot copy the utility over to the floppy. Why? Because Ubuntu doesn't seem to even recognise the floppy drive at all.

Now.. The floppy drive works, as does the disk as I can boot msdos from it by booting without the Ibex CD in the drive. So theres not a hardware problem, or a problem with the disk itself.

So, how can I fix this?

[http://forums.vnunet.com/thread.jspa?threadID=149144&tstart=0](http://forums.vnunet.com/thread.jspa?threadID=149144&tstart=0)

---

### Post by howefield on 2009-02-07
Try the terminal command

```
sudo modprobe floppy
```

You'll then be able to mount/unmount the drive.

I think to make it boot the floppy each time you boot the computer, you would need to add the floppy module to /etc/modules

---

