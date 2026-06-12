---
title: "trying to get Nautilus to recognize external HD but not automount"
date: 2014-07-14
forum: Desktop Environments
---

### Post by jourosis on 2014-07-14
Sorry if this question has been answered, but I've been searching on/off for the past few months without a clear explanation of such.

I am trying to get my external hard drives (usb) to be recognized by Nautilus and/or the system in general but not be automounted. In short, I want them treated like my windows partition (dual-boot w/ Win7) is treated. The icon is shown in Nautilus' "Devices" area but isn't mounted until clicked. I know this is possible because I had it set up like this once, then foolishly reinstalled when I changed cases thinking I had everything backed up. The end goal of this is I have a photo-processing script that uses gvfs-mount to mount, then copy to, then unmount an external drive that's only used for storing the backups. Right now there are no relevant entries in fstab nor do I have any udev rules in place (as far as I can tell). Current automount location is /media/Elements but folder is not actual created, only exists when drive is mounted via Nautilus.

To be clear, I am not trying to figure out how to disable ALL automounting, just for a specific drive. Thanks and Cheers!

---

