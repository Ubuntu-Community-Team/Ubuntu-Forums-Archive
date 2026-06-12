---
title: "delete partitions?"
date: 2005-08-30
forum: Desktop Environments
---

### Post by tmasboa on 2005-08-30
how do i delete :roll:  partitions? \\:D/   :? THanks. 

edit: where can I get fdisk?

Also, how do I burn an iso to a blank cd if I have to? 

Thanks again!

edit: is there command line utility? I would prefer that

edit: I tried Gparted, but it gave me;

(gparted:8766): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

---

### Post by danns on 2005-08-30
fdisk should be located in /sbin (which may not be in your path).  You can also find cfdisk in the same location.

To burn a cd from the command line you simply need to issue:

cdrecord speed=?? dev=?? iso_image

I like to add verbose mode to do that.  You should be able to burn right to the device:

cdrecord -v speed=15 dev=/dev/hdc ubuntu_ppc.iso

That would burn the iso ubuntu_ppc.iso with a speed of 15 to the cdrecorder - the first device on the second ide controller.

There are a whole lot of other options to cdrecord so peruse the man-page and look at the cdburing howto.  You can find this on the [Linux Documentation Project](http://www.tldp.org) or grab the howtos via synaptic.

---

