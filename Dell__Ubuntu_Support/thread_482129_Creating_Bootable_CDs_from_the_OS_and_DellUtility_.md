---
title: "Creating Bootable CDs from the /OS and /DellUtility Partitions"
date: 2007-06-23
forum: Dell  Ubuntu Support
---

### Post by mark on 2007-06-23
Since I don't like trusting anything to a single failure point source (the HDD) and I can't order bootable CD(s) from Dell, I'm looking to create bootable images (ISOs) from the /OS and /DellUtility partitions from my Inspiron E1505N laptop. Having never done this before, I'm looking for a little help...

Is it just a matter of using the mkisofs (or genisoimage) utility? If anybody has done this before, some guidance would be appreciated - particularly any desired/required options or switches to the above commands...

I tried: ```
genisoimage -o /home/mark/Image/restore.iso /media/sda2
```
which produced a non-bootable image.  I also tried: ```
genisoimage -hard-disk-boot -o /home/mark/Image/restore.iso /media/sda2
```
which gave me no image but the error message: ```
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing boot image name, use -eltorito-boot option.
```
I the tried: ```
genisoimage -hard-disk-boot -eltorito-boot -o /home/mark/Image/restore.iso /media/sda2
```
which resulted in: ```
genisoimage: Uh oh, I cant find the boot image '-o' !
```

Obviously, I'm doing something wrong...what do I give -eltorito-boot as an argument?

---

### Post by mitchellthegreat on 2007-06-24
If you're trying to make copies of ubuntu, download it off the site and burn it to a CD.
If you're trying to intall windows programs, use wine.
If you're trying to confuse me, keep up the good work! :p

---

### Post by neptho on 2007-06-24
If you want to recreate a reinstallation CD, you need to have a bootable image.  Just copying things onto an ISO will not work.

The easiest way you may do this is by making the Ubuntu Feisty Fawn CDs.  Really.  There's very little else that [isn't just added on afterwards](http://linux.dell.com).

---

### Post by Tethtibis on 2007-06-26
yes, it's much easier to just get an ubuntu distro, and use a program like infrarecorder to make it bootable from an iso image.

---

