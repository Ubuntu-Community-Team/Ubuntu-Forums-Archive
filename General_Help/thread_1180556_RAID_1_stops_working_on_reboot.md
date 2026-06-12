---
title: "RAID 1 stops working on reboot"
date: 2009-06-07
forum: General Help
---

### Post by bertmanphx on 2009-06-07
Hello,
I'm running 9.04 32bit here, as a file server using NFS.

what I want to share, is a  raid 1 directory.
The main OS is installed on one 320 GB drive.
I have two 500GB drives that I have configured with RAID 1 using mdadm, and mounted as /media/raid

This all seems to work fine, until I re-boot.  Then I get this error.
root@titan:/home/robert# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdb[1](S)
      488386496 blocks

Both drives were clean when I installed them.  I can stop the array, and re-add the /dev/sdb drive, wait for it to sync, and attempt it again, but have the same results.

Upon reboot, it does not work again.

Any help is appreciated.

Thanks,

bertmanphx

---

### Post by fjgaude on 2009-06-07
What do you have for the array in your **fstab** file?

---

### Post by bertmanphx on 2009-06-07
Hello,
the raid array is mounted in fstab as:
/dev/md0 /media/raid ext4 defaults 0 0

It has been up all night, and after a couple re-boots....perhaps it's fine now.

bertmanphx

---

### Post by ronparent on 2009-06-08
This is a problem reported by several people. Some bug exists with 9.04, only in some instances, in that raid drives are not mounted on boot. Apparently for some reason the raid is not active when fstab is processed. You might find a work around or a lead to one posted in the servers forum.

---

### Post by fjgaude on 2009-06-10
What does your /etc/mdadm/mdadm/conf file look like?

You may have to re-create it using this command:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

At least that is one way. Let us know how things are going.

---

### Post by pizzapieguy on 2009-07-04
bertmanphx, did you ever resolve this?  I was recently experiencing what seems to be the exact same issue where one of my devices was getting assigned to a md_d0 RAID somehow during boot.

My fstab entry was very similar except I used the UUID of my /dev/md0 device and am using ext3 still.

  I have a similar setup where I boot from a non-RAID device but have a RAID device in-system for storage.  I probably did not find the root cause, but I did get things working.

I'm guessing you have this  line in /etc/mdadm/mdadm.conf (only because I did)

```

DEVICES partitions

```I edited the file to specify the particular devices in my RAID1, for example

```

DEVICES /dev/sdb /dev/sdc

```Then I specified that those devices were to be used to create my RAID1 with this line

```

 ARRAY /dev/md0 devices=/dev/sdb,/dev/sdc
 
```My RAID1 now is correctly assembled on boot.

---

