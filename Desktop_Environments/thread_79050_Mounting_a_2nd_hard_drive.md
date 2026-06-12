---
title: "Mounting a 2nd hard drive"
date: 2005-10-19
forum: Desktop Environments
---

### Post by filemanager on 2005-10-19
Before upgrading to Breezy, I want to backup my /home folder.

I recently added a second hard drive to my computer, and I want to backup my /home folder to it, but I'm not sure how to mount it :confused: 

It was my husband's old Windows XP hard drive, but I deleted everything off of it. (If that makes  any difference) 

Can anyone help? I'm psyched for Breezy!

---

### Post by SeanCallan on 2005-10-19
This worked for me.  My device was called /dev/hdb yours may be different.  Also, I had it mounted to a folder called second you can change that.

```

mke2fs -j /dev/hdb1
mkdir /mnt/second
mount -t ext3 /dev/hdb1 /mnt/second
```

Also if you go into terminal and run "sudo disks-admin" you should see the HD there.  You can format it and mount it via the GUI which may make it easier for you.

:)

---

### Post by mbollenb on 2005-12-13
I would like to add that the first line of the code above formats your hard drive to all the Linux Newbies.  I just ran that and lost 3 years of development files due to being new to linux.  I figured it was just mounting my hard drive

---

### Post by zoiks on 2005-12-13
Before you can mount it for read/write operations, you must

0) (!!) Figure out which device it is (probably /dev/hdb, /dev/hdc, or /dev/hdd, depending on how you connected it)
1) Partition it
2) Format it

Make sure you perform step #0 correctly, or you'll lay your data to waste big time.

Let's say the drive happens to be /dev/hdc.  You can run "sudo fdisk /dev/hdc" to partition the drive (it might already be partitioned).  My suggestion is create 1 partition for the whole drive and label it a Linux partition.  The partition you create would then be known as "/dev/hdc1".

Once you partition it, you should reboot the computer so that the partition table is properly read.  Then you can run the mkfs (or mke2fs, etc., with sudo) command to format the partition (using the correct partition name).  This sets the partition up with a file system.  Then make a directory to mount it to and finally mount the drive, as SeanCallan has described above.  You can confirm the drive is mounted by entering "df" or "sudo cat /etc/mtab" at the command line and examining the output.

Now you can read and write to the drive (though it'll simply show up as data within your file system).  But be careful!  Doing this for the first time or three can be very dangerous to your data, so think about your steps.

You'll also have to worry about file ownership since I think by default the drive will be mounted as owned by root.  When you copy, you can use the '-p' or '-a' option to preserve ownership of the data, or just do a "chown -R" command later to change the ownership back.

Uh, oh yea, there's no warranty associated with the above advice.  ;)  Good luck!

---

### Post by quietglow on 2005-12-13
[QUOTE=mbollenb]I would like to add that the first line of the code above formats your hard drive to all the Linux Newbies.  I just ran that and lost 3 years of development files due to being new to linux.  I figured it was just mounting my hard drive[/QUOTE]

Ouch.

These posts have good advice, but I'm getting rather addicted to the "disks" GUI! System>Admin>Disks will give you an interface where you can format, mount, etc all your drives--including ones just added. Really nice.

---

### Post by autocrosser on 2005-12-13
Also remember Gparted--works great! You might add your "discovered" drive to the /etc/fstab--that way you have access to it every time you boot--

Mine looks like this-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hdb10      /opt            ext3    defaults        0       2
/dev/hdb8       /tmp            ext3    defaults        0       2
/dev/hdb7       /usr            ext3    defaults        0       2
/dev/hdb9       /var            ext3    defaults        0       2
/dev/hdb4       /mnt/osx        hfsplus defaults        0       0
/dev/hdb3       none            swap    sw              0       0
/dev/hda3       /mnt/osx4       hfsplus defaults        0       0
/dev/hda5       /mnt/root       ext3    defaults        0       0
/dev/hda6       /mnt/home       ext3    defaults        0       0
 /dev/hda7       /mnt/opt        ext3    defaults        0       0

I have two internal drives & two Ubuntu installs that I sync.


(By the way---quietglow---THUMBS UP on the Flying Spagetti Monster conversion!!!)

---

### Post by zoiks on 2005-12-15
[QUOTE=quietglow]Ouch.

These posts have good advice, but I'm getting rather addicted to the "disks" GUI! System>Admin>Disks will give you an interface where you can format, mount, etc all your drives--including ones just added. Really nice.[/QUOTE]

That's pretty sweet.  I hadn't seen that before, been too used to doing these things the hard way.  Learn something new every day!

---

### Post by juicybananahead on 2006-05-05
Ouch.

---

