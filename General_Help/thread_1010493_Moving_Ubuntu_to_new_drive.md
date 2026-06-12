---
title: "Moving Ubuntu to new drive"
date: 2008-12-13
forum: General Help
---

### Post by csc2ya on 2008-12-13
I've currently got my laptop configured in the following way:

Vista Ultimate on internal drive
MacOSX Kalyway on internal drive
Ubuntu Ultimate on External USB Drive using approximately 119GB
Backup of Vista on External Drive using approximately 118GB

I use the windows bootloader, with added items for macosx and linux, which start the darwin and grub bootloaders before booting the default option in those respective bootloaders.

The external drive that i've got linux on is failing (takes a few goes to get it spin up if it's been off for a while, and disconnects every few days meaning linux crashes, and I have to reboot)

I'm going to get a new drive to replace it soon, and plan to up the size to 1TB.

I want to have the same partition layout on the new drive, but bigger (vista backup partition will be approximately 500GB, and linux partitions will occupy the other 500GB) (I know I won't have exactly 1TB to play with, but I can't be bothered with the hassle of working it out)

If I cloned the drive, the partition sizes would remain the same.

If I booted from the ubuntu CD, would simply copying all the files over after creating the partitions mean grub would still work and linux would be bootable?

It's not a problem if I do have to redo all the bootloaders, but i'd rather avoid that if possible.

Thanks in advance.

---

### Post by lensman3 on 2008-12-13
I would do this:

0. Start up in single user mode with ALL the old partitions in read-only.  This way the file systems are not changing under you.

1. Partition and mount your new drive with the empty partitions.

2. mount each of the partition under say a temporary mount directory (In this case lets call it /mnt).  So you would have a /mnt/boot, /mnt/root->/,
/mnt/usr and so on.

3. Copy each partition over to the new disk using
    cp -Rpv -x /usr /mnt/usr    

and so on for each partition.  The -x causes cp to stay on one  partition at a time.  It won't follow the other mounted partitions.  The -R recursively goes down each directory tree and -p preserves the creation times etc.   Once you copy a partition, do a "sync" to write everything out.  (The new disk is not mounted read-only only the old disk).

    OR
         cd <FROM DIR>
         tar cf - . | ( cd <TARGET DIR> ; tar xBf - )

4. Once everything is copied. Remove the old drive and install the new drive in its place.

5. Repair the boot from your boot cd.


One thing you might try is:

        "dd if=/dev/sda of=/dev/sdb"

This will copy track-for-track and byte-for-byte the entire disk sda to sdb.  In this case your are copying devices not files and filesystems.  It might even preserve the boot sequence.  The bad thing is that any bad tracks will ALSO be copied to the new device.  It will also preserve your old partition layout (I think), so that if you start with 500 Gbytes your new disk will have only 500 Gbytes of accessible disk.  You lose half the 1 Tbyte disk.  You might be able to use /sbin/fdisk to extend the last partition without destroying the data on the disk.

I think you can get to runlevel 1 by running as superuser from a command prompt "telinit 1".  This should dump you to a text screen in seconds.  To exit runlevel 1, enter cntl-d (for logout).  See the file /etc/inittab for the various runlevels.


Good luck.

---

### Post by CatKiller on 2008-12-13
> **lensman3 said:**
> One thing you might try is:

        "dd if=/dev/sda of=/dev/sdb"

This will copy track-for-track and byte-for-byte the entire disk sda to sdb.  In this case your are copying devices not files and filesystems.  It might even preserve the boot sequence.  The bad thing is that any bad tracks will ALSO be copied to the new device.  It will also preserve your old partition layout (I think)

That's correct. The boot sequence, partition layout and UUIDs will remain unchanged, meaning there is nothing else to do. You can then expand the partitions in GParted or your partition editor of choice to get the sizes that you want.

It's not a quick process, but it is complete (it will copy empty space bit-for-bit, too). The warning about bad sectors is a serious one, though. If your hard drive has already been failing, then sectors at random could have been adversely affected, especially if the power has suddenly been interrupted. You should seriously consider backing up the data that you wish to keep and doing a re-install to ensure that the data used to run the operating system has not been compromised. Otherwise that could potentially lead to a steady increase in errors over time. This would be for both operating systems.

---

### Post by csc2ya on 2008-12-13
Thanks for the replies. I'll give both of them a go once i've got the new drive. If they don't work, i'll backup all my data and do a fresh install on the new drive.

I won't mark this as solved just yet, but will do once i've got the drive and have it working.

Thanks again:cool:

---

