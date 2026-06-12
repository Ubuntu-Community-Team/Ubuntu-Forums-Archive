---
title: "Disable GNOME automount on per device basis"
date: 2008-07-19
forum: Desktop Environments
---

### Post by kkjaergaard on 2008-07-19
Is it possible to disable GNOME automount on a per device basis?

The case is that I have a USB stick with two partitions, and I only want GNOME to automount the first of them.

---

### Post by kaibob on 2008-07-19
> **kkjaergaard said:**
> Is it possible to disable GNOME automount on a per device basis? The case is that I have a USB stick with two partitions, and I only want GNOME to automount the first of them.
I am far from an expert on this issue, but perhaps you could include the flash drive in fstab and use the auto option for one partition and noauto for the other. More of a guess than an informed opinion but...

The following is a good resource on fstab:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by kkjaergaard on 2008-07-20
> **kaibob said:**
> ...you could include the flash drive in fstab and use the auto option for one partition and noauto for the other.

I think that is a good solution for my computer, but I was thinking more about a *portable* solution so that no matter which GNOME environment (and eventually others as well) I use the USB stick on, only the last partition is automounted.

Thanks anyway.

---

