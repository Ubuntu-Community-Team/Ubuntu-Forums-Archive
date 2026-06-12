---
title: "why lilo and not grub???"
date: 2006-08-10
forum: Desktop Environments
---

### Post by saracen on 2006-08-10
I just finished an install of Dapper 6.01 (just released - LTS with all the updates). I'm setting it up on an LVM that spans over 3 drives.  For some reason at the end of the installation it wants to set up LILO and not GRUB.  I have no option to choose grub.  When I reboot after the installation, I get a grub error 22 and the system hangs!

Please help... I really need to get my system back up and running.

---

### Post by saracen on 2006-08-10
Could it be because I put /boot in the LVM?  Does that work... having /boot in the LVM?

---

### Post by John.Michael.Kane on 2006-08-10
These may be of some help.
[**Installation/RAID1**]("https://help.ubuntu.com/community/Installation/RAID1")
[**LVMOnRaid**]("https://help.ubuntu.com/community/Installation/LVMOnRaid")

---

### Post by saracen on 2006-08-11
OK, this situation is really frustrating me so i'd really appreciate some help.  I'm using an LVM, but I'm not using RAID.  The reason I'm using LVM is so that I can merge my two 500GB drives.  Do I have to use RAID?

I tried putting /boot on a separate primary partition of its own and not inside the LVM.  This time the installation used GRUB not LILO, but I"m still getting the same error.  I think it has to do with my /boot/grub/menu.lst file.  

For my setup I have 3 SATA drives - 2x500GB and one 120GB drive.  During the install I created a 100MB partition on one of the 500GB drives and mounted it as /boot.  Then I created a volume group on the rest of the space and created 3 logical volumes - root (10GB), swap (1GB), and home (the rest of the space).  The install was successful and I choose to install GRUB on the master boot record.  When I reboot I get Error 22.

So I booted into the LiveCD to check out the situation.  The logical volumes are ok - I checked them with the lvdisplay command.  The /boot partition is on /dev/sdb1 and the logical volumes are on /dev/Mongo/root, /dev/Mongo/home and /dev/Mongo/swap.  Mongo is the name I chose for my volume group.

I mounted the /boot parition in the live CD and checked out the menu.lst file.  It had the following for the first OS:

```
title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/Mongo/mongo-root ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot
```

I don't know why it had that path for root.  I changed it to root=/dev/Mongo/root.  I also changed the root hard drive to (hd1,0) since my /boot parition is on /dev/sdb1 and I checked the device.map file which showed hd1 is mapped to /dev/sdb.  I rebooted... but still no dice.  

Don't know what to do really... I thought that I had fixed it.  It's really frustrating and I could really use some help...

---

### Post by saracen on 2006-08-11
I read something about using mkinitrd to create a new initrd file... could that be my problem?  if so then based on the above setup, what is it exactly that i have to do?

---

### Post by saracen on 2006-08-11
anyone?

---

