---
title: "Recover Ubuntu boot entry"
date: 2009-04-22
forum: General Help
---

### Post by inxygnuu on 2009-04-22
Hello, I just installed Sabayon Linux, and I created a shared boot drive but I overwrote the menu.lst. I knew this would happen, but I thought that Sabayon would put an entry for Ubuntu in there, and move the files elsewhere. I looked around, and there is no entry for Ubuntu (Jaunty) around. I still have all of the files that Jaunty needs to boot up, other than the GRUB entry. Is there a way to recover this?

Thanks,
3v4n

---

### Post by DagMan on 2009-04-23
If you originally had your /boot directory on the same partition as / in ubuntu, then you can always mount that partition in saybayon and get the entry from there.

If that isn't the case, then you'lle want to add it in manually to your menu from saybayon.  Mine looks like this with the most recent generic kernel.  If you didn't have the most recent kernel installed then you can edit that part.  Also You'lle need to edit the parts that say uuid for now.  I'm bolding the differances in the two entries below.

title		Ubuntu 9.04, kernel 2.6.28-11-generic
**uuid		868dca04-0a93-47aa-aa46-0aaa5d243847**
kernel		/boot/vmlinuz-2.6.28-11-generic root=**UUID=868dca04-0a93-47aa-aa46-0aaa5d243847** ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet


so editing out the uuid to the other format, it would look maybe something more like this:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
**root            (hd0,1)**
kernel		/boot/vmlinuz-2.6.28-11-generic root=**(hd0,2)** ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

To explain the differances between the above and the below, UUID is an identifier of the partition, where root (hd0,1) tells grub which partition by disk and hardrive starting with 0.  /dev/sda3 is (hd0,2) as grub counts from 0 upwards and the OS goes from 1 upwards.
The line that begins with root below the line that says title tells grub where to find the /boot partition, and the entry in the kernel line root=(hd0,2) tells grub where to find the / partition.

You may find it helpfull also though, if you haven't repartitioned and moved data, to mount your ubuntu root partition and look at the /etc/fstab file, and get the UUID values from there instead.
I feel I should note that if you have resized partitions or moved data from one partition to another, that you would have to replace the uuid parts in fstab with the name as it would appear in /dev, for example if /boot used to be at /dev/sda3 and is now /dev/sda1 then the uuids aren't going to work.. but that would be a separate issue, and a small one.

Good luck.  If it sounds daunting, don't worry... just post back what's happening.  It's a fixable problem.

---

### Post by inxygnuu on 2009-04-23
Thanks!:) Got it working! All i needed was how to obtain the UUID, but you told me how to do that. I changed your script to something like:

title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=868dca04-0a93-47aa-aa46-0aaa5d243847 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

Now I just need to redo my shared home partition:-k...

Thanks a ton\\:D/,
3v4n

---

