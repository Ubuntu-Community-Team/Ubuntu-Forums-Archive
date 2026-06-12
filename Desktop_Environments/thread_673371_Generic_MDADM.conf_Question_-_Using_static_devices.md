---
title: "Generic MDADM.conf Question - Using static devices = bad?"
date: 2008-01-20
forum: Desktop Environments
---

### Post by fermulator on 2008-01-20
So first off, I'm a beginner with Linux software RAID, and I've selected MDADM.

Most of my knowledge comes from:
[LIST]
[*][http://linux.die.net/man/5/mdadm.conf](http://linux.die.net/man/5/mdadm.conf)
[*][http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)
[/LIST]

Now, to the setup.  My /etc/mdadm.conf look as follows:
> ARRAY /dev/md0 level=raid0 num-devices=2 UUID=c4880fbc:fc2dbdda:01f5a1db:50a22640
   devices=/dev/sdg1,/dev/sdh1

If my understanding is correct, the line ARRAY defines our array with various parameters.  The one I'm interested in discussing is the "devices=" parameter.

The two devices, /dev/sdg1 and /dev/sdh1 are indeed the two drives I'm using for my RAID0 (Performance Stripping) array.


The question:
> Can I define this list of devices by their UUID instead?

The reason for this is of course because if the physical arrangement of drives change, my two drives supposedly in the array might no longer be /dev/sdg1 and /dev/sdh1.  So if my 'array drives' become different devices (say /dev/sdx1 and /dev/sdz1), would the array not collapse?  This is the point of UUID, to avoid this potential catastrophe.

If anyone could provide some experience/knowledge it would be greatly appreciated.

---

### Post by fuex on 2008-01-21
Im not an expert at all, on this topic. So not all might be true:

The way to keep a certain fixed  device naming scheme, even though you change disks etc.  is achieved through writing udev-filesystem rules...  NOT  mdadm.conf or alike.

you can specify a device with UUID (physical property I guess)  always to have the same name. as a consequence,  there's no need for UUIDs in mdadm.conf.
the reason why you specify an UUID for the array itself (the 'meta' device) I believe is to use it again with udev-fs and so on. because it's a new device which should also have an UUID.

Hope that sounds reasonable!

---

