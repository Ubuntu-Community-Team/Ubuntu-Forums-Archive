---
title: "Disable one swap partition"
date: 2009-03-28
forum: General Help
---

### Post by cometa2k7 on 2009-03-28
Ok, perhaps a strange problem, but it's annoying me.

Basically, I have installed a Jaunty Alpha on my computer, in a dual-boot with Intrepid. I have two swap partitions on my harddrive, and I want each to use only one. Intrepid does this, but Jaunty seems to use both.

Intrepid was installed with only one swap on the system at the time, with Jaunty I had both set up.

How can I prevent Jaunty from using both swap partitions, and make it instead use just one.

And out of interest, is it any benefit having two swap partitions. I hobernate my computer, and that means that I do have to option to boot one operating system with the other hibernated. When I did this with Jaunty, and booted Intrepid, it killed the hibernation data. Would this ever happen with Jaunty using one swap partition?

Thanks in advance.

---

### Post by dcstar on 2009-03-28
> **cometa2k7 said:**
> Ok, perhaps a strange problem, but it's annoying me.

Basically, I have installed a Jaunty Alpha on my computer, in a dual-boot with Intrepid. I have two swap partitions on my harddrive, and I want each to use only one. Intrepid does this, but Jaunty seems to use both.

Intrepid was installed with only one swap on the system at the time, with Jaunty I had both set up.

How can I prevent Jaunty from using both swap partitions, and make it instead use just one.

And out of interest, is it any benefit having two swap partitions. I hobernate my computer, and that means that I do have to option to boot one operating system with the other hibernated. When I did this with Jaunty, and booted Intrepid, it killed the hibernation data. Would this ever happen with Jaunty using one swap partition?

Thanks in advance.

As the post at the top of this forum states, all pre-release software questions go to the development forum.

---

### Post by coffeecat on 2009-03-28
I'll try and be more helpful. As this involves multibooting different versions and the use of swap partitions, this forum seems quite appropriate.

Besides, this question is nothing specifically to do with a development version per se.

Anyway, **cometa2k7**, I think we can solve this with the /etc/fstab of Jaunty. Post the contents of fstab for both Jaunty and Intrepid, and then we can see how to allocate one swap to J and one to I. Then you shouldn't run into those hibernation problems.

---

### Post by dcstar on 2009-03-28
> **coffeecat said:**
> I'll try and be more helpful. As this involves multibooting different versions and the use of swap partitions, this forum seems quite appropriate.

**Besides, this question is nothing specifically to do with a development version per se.**

Anyway, **cometa2k7**, I think we can solve this with the /etc/fstab of Jaunty. Post the contents of fstab for both Jaunty and Intrepid, and then we can see how to allocate one swap to J and one to I. Then you shouldn't run into those hibernation problems.

Of course it does, new versions invariably work differently and there is little point in posting a problem in a forum **where the overwhelming majority are not using the unreleased version** and therefore cannot replicate a problem or probably offer any useful assistance with a problem.

That is exactly why the developers of pre-release versions **demand** that issues are put in the development forum (as a condition of using the pre-release software), because they are using that actual release and they want to know of these things so they can be addressed before official release.

Not posting things in the development forum basically ensures that the released software has more problems - and therefore will cause more problems for more users - that it could of.

---

### Post by cometa2k7 on 2009-03-29
> **dcstar said:**
> Of course it does, new versions invariably work differently and there is little point in posting a problem in a forum **where the overwhelming majority are not using the unreleased version** and therefore cannot replicate a problem or probably offer any useful assistance with a problem.

That is exactly why the developers of pre-release versions **demand** that issues are put in the development forum (as a condition of using the pre-release software), because they are using that actual release and they want to know of these things so they can be addressed before official release.

Not posting things in the development forum basically ensures that the released software has more problems - and therefore will cause more problems for more users - that it could of.

I understand what you mean, but I felt that this was more of a general issue which I wanted resolved, it wasn't a technical issue specific to the Jaunty Alpha. If it was a problem with Jaunty, I would have posted it in there.

This issue may be relevant to anyone dual-booting two linux distributions.

---

### Post by cometa2k7 on 2009-03-29
Jaunty /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=8b0a29cc-e9df-4c3c-82a3-fe45bb55923a /               ext2    relatime,errors=remount-ro 0       1
# /home was on /dev/sda11 during installation
UUID=6bff6857-ea7a-4d1b-92e2-8c332a68ed96 /home           ext4    relatime        0       2
# none was on /dev/sda10 during installation
UUID=b621c663-c714-46fd-a39b-6d45ad5d8acb none            swap    sw              0       0
# none was on /dev/sda6 during installation
UUID=7e506e89-5856-4b2f-b727-db92c5408ecf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Intrepid /etc/fstab
```
proc            /proc           proc    defaults        0       0
UUID=32d8120d-5e8d-44ea-9309-17ff55a32d0f /               ext2    relatime,errors=remount-ro 0       1
UUID=fab2e119-e0a1-4a75-a648-f8ec1bc05a6a /home           ext3    relatime        0       2
UUID=7e506e89-5856-4b2f-b727-db92c5408ecf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I'm assuming that I just comment out the second swap entry on Jaunty, I'll go and try it.

It worked, thanks.

---

### Post by coffeecat on 2009-03-29
> **cometa2k7 said:**
> I'm assuming that I just comment out the second swap entry on Jaunty, I'll go and try it.

It worked, thanks.

I'm glad you've sorted it. :) Yes, normally you'd only have one swap partition, unless you want to avoid that issue with hibernating - as you've discovered.

I had something similar happen to me with Hardy. I'd mistakenly left an old swap partition lying around on sdb. As you do :wink: - long story. The installer set up two entries in fstab. I only discovered this when I tried to delete the sdb swap in Gparted from within Hardy.

---

