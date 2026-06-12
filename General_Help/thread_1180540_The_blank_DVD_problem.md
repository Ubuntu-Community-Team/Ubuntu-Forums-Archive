---
title: "The blank DVD problem"
date: 2009-06-06
forum: General Help
---

### Post by Valeofruin on 2009-06-06
The problem:

Blank DVD's Don't work on Ubuntu 9.04 (64 bit)

The Solution: Make sure you're using the right hardware first.

---

### Post by lisati on 2009-06-06
> **Valeofruin said:**
> 
Why will ubuntu not recognize blank DVD's and only blank dvd's?

Typo? Did you mean "only blank CDs"?

I hadn't actually noticed any problem. One possibility: Not all burners are created equal - does your machine have a CD-birner/DVD-reader drive?

---

### Post by Valeofruin on 2009-06-06
> **lisati said:**
> Typo? Did you mean "only blank CDs"?

I hadn't actually noticed any problem. One possibility: Not all burners are created equal - does your machine have a CD-birner/DVD-reader drive?

/stands corrected

Making sure I test this on the proper drive

---

### Post by Krupski on 2009-06-06
> **Valeofruin said:**
> 3 different manufactures of DVD's were tested, none of them are detected in Ubuntu 9.04 amd64.


I'm running Ubuntu 9.04 64 bit and using a HP 1170i SATA DVD writer. I just stuck in a blank DVD+R disk and it was recognized just fine.

I inserted the disk, about 5 seconds later a disk icon called "Blank DVD+R Disc" popped up on my desktop.

I suspect your problem is not an Ubuntu problem...

---

### Post by Valeofruin on 2009-06-07
> **Krupski said:**
> I'm running Ubuntu 9.04 64 bit and using a HP 1170i SATA DVD writer. I just stuck in a blank DVD+R disk and it was recognized just fine.

I inserted the disk, about 5 seconds later a disk icon called "Blank DVD+R Disc" popped up on my desktop.

I suspect your problem is not an Ubuntu problem...

Edit: It is in fact a hardware problem.

For starters it helps if all the pcs are dvd r/rw

---

### Post by Krupski on 2009-06-07
> **Valeofruin said:**
> Edit: It is in fact a hardware problem.

For starters it helps if all the pcs are dvd r/rw

I don't know what to tell you. It works fine for me.

I have an IDEA though... believe it or not I was thinking about this last night (my mind always races in bed). Anyway, I was wondering what's different about my machine than yours.

I realized that in my fstab file, I removed the mount information for the CD drive and let UBUNTU just automount whatever it finds.

The fstab entry is looking for an ISO-9600 filesystem (which of course isn't on a blank disk). My system doesn't have that entry because I removed it.

Try this: Open up your "/etc/fstab" file in an editor, find the line for the CD (the device is called "/dev/scd0" and comment it out by placing a "#" as the first character of that line.

Then, reboot and see if your system will recognize blank DVD disks.

-- Roger

---

### Post by Valeofruin on 2009-06-07
> **Krupski said:**
> I don't know what to tell you. It works fine for me.

I have an IDEA though... believe it or not I was thinking about this last night (my mind always races in bed). Anyway, I was wondering what's different about my machine than yours.

I realized that in my fstab file, I removed the mount information for the CD drive and let UBUNTU just automount whatever it finds.

The fstab entry is looking for an ISO-9600 filesystem (which of course isn't on a blank disk). My system doesn't have that entry because I removed it.

Try this: Open up your "/etc/fstab" file in an editor, find the line for the CD (the device is called "/dev/scd0" and comment it out by placing a "#" as the first character of that line.

Then, reboot and see if your system will recognize blank DVD disks.

-- Roger

Testing, will edit.

Edit: No improvement.

I'm gonna upgrade the DVD drive.. its not that expensive, and i need more RAM anyways, and see if that works

---

### Post by VMC on 2009-06-07
What's the output of this command, from a terminal:

```
wodim -checkdrive
```

---

### Post by Krupski on 2009-06-07
> **VMC said:**
> What's the output of this command, from a terminal:

```
wodim -checkdrive
```

Wow. What the heck is "wodim"? Never heard of it.

Anyway, for what it's worth, here's what my machine replied:

```

root@michael:/# wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HP      '
Identification : 'DVD Writer 1170d'
Revision       : 'DH22'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

```


Note that my setup (Ubuntu 9.04 64 bit, HP DVD 1170i internal SATA CD/DVD writer, 4 GB ram, Intel DQ45CB motherboard, Intel Q9650 CPU) does indeed recognize blank DVD disks (mine are DVD+R if that matters).

Here's my /etc/fstab file. Note that I removed the default "/dev/scd0" entry:

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                 <mount point>   <type>  <options>       <dump>  <fsck>

# proc
proc                            /proc           proc    defaults        0       0

# root
/host/ubuntu/disks/root.disk    /               ext3    loop,errors=remount-ro 0       1

# boot
/host/ubuntu/disks/boot         /boot           none    bind            0       0

# swap
/host/ubuntu/disks/swap.disk    none            swap    loop,sw         0       0

```


Notice that I am running Ubuntu mounted with loop (that is, a WUBI install). My Ubuntu "disk" is actually a 30 gb file on an NTFS drive on my machine. This really shouldn't matter though. In fact, I have a Sony CD/DVD writer in my file server box (running Ubuntu Server 9.04 64 bit) and it also works.

Only problem I ever had with stuff NOT working was when my older Ubuntu 8.10 wouldn't recognize the NIC on my new motherboard (an Intel E1000E that didn't have a driver for yet). I downloaded the driver from Intel and it just worked.

Ubuntu 9.10 has this driver included, so my "problems count" has dropped from one to zero!  :)


-- Roger

---

