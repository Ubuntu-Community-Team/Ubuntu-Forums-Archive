---
title: "gparted - cannot unmount /dev/sda1 or partition"
date: 2008-12-13
forum: General Help
---

### Post by lamikins on 2008-12-13
Hallo,

I'm trying to create a partition for XP on my xubuntu system, as I need the MS office suite for some work.  With gparted the "=> resize/move" item was greyed out so I went to unmount /dev/sda1 and got:

"Could not unmount /dev/sda1

The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually."

I never really expected this to work, as to my way of thinking this would involve unmounting the working drive...  or something to that effect. I know this is a common thing to be doing, and the solution is most likely obvious/trivial (though not to me).  

Could someone possibly point me in the right direction?

---

### Post by Elfy on 2008-12-13
Use your buntu livecd or a partition editor livecd, I use partedmagic and / will be unmounted and you can do as you see fit

---

### Post by lamikins on 2008-12-14
Cool, thanks - I shall try this now!

---

### Post by lamikins on 2008-12-15
Okay - is there any obvious way of creating the partition without LiveCD?  With or without Gparted et al...  I ask having just remembered I installed off alternate, so live = nono.

---

### Post by RomanIvanov on 2008-12-15
Live CD did worked for me, I found USB live:
UNetbootin + gparted-live-0.3.9-4.iso. Easy to install and use

---

### Post by Elfy on 2008-12-15
You can I believe do it but it's not something I have experience or knowledge of.

I actually don't use a buntu livecd for partitioning myself, I use partedmagic, it also has some other tools on the disc which are quite useful - small download burn as iso and boot with it

[http://wiki.partedmagic.com/index.php/Downloads](http://wiki.partedmagic.com/index.php/Downloads)

You can also get gparted which is more or less the same size

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by lamikins on 2008-12-15
Ohh k - partedmagic to unmount "/" and form the partition, and I suppose one reboots with the livecd in drive...  Once again, i'll try this!  thanks again

---

### Post by Elfy on 2008-12-15
yep you got it - get yourself a copy of [supergrub]("http://www.supergrubdisk.org/") as well and you shouldn't need much more in the way of tools :)

---

