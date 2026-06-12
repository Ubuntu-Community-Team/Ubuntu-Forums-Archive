---
title: "Accessing HDD partitions through Linux"
date: 2009-02-24
forum: General Help
---

### Post by Scootymad on 2009-02-24
How do I access my HDD partitions through Ubuntu?

---

### Post by Slim Odds on 2009-02-24
> **Scootymad said:**
> How do I access my HDD partitions through Ubuntu?

That's a really vague question. Care to give any details?

---

### Post by Scootymad on 2009-02-24
I need to know how i can view my hards drive and partitions on ubuntu

---

### Post by Slim Odds on 2009-02-24
> **Scootymad said:**
> I need to know how i can view my hards drive and partitions on ubuntu

That's not detail.

If you plug in some type of removable media, it should show up automatically.

If it's a fixed drive (like IDE, or SATA), then you need to mount it manually or add it to your /etc/fstab to mount it automatically.

---

### Post by Scootymad on 2009-02-24
Yes its a sata HDD, as in the HDD inside the computer.

How do I mount it?

---

### Post by Wayne_V on 2009-02-24
cat /proc/partitions

cat /proc/scsi/scsi

dmesg | grep "sd[abcdefg]"

---

### Post by Scootymad on 2009-02-24
> **Wayne_V said:**
> cat /proc/partitions

cat /proc/scsi/scsi

dmesg | grep "sd[abcdefg]"


And what on earth does that mean?

Im new to this linux jargon

---

### Post by Wayne_V on 2009-02-24
Reading man pages is the best way to learn!

See 'man proc', 'man dmesg', 'man grep', 'man mount', etc

---

### Post by Scootymad on 2009-02-24
> **Wayne_V said:**
> cat /proc/partitions

cat /proc/scsi/scsi

dmesg | grep "sd[abcdefg]"

All I get is permissions denied :(

---

### Post by Wayne_V on 2009-02-24
What version of ubuntu are you running?  In my Ibex installation I don't need to be root to access those files.

Run the commands with sudo to get around that.

---

### Post by Hobgoblin on 2009-02-24
> **Scootymad said:**
> How do I access my HDD partitions through Ubuntu?

Click on places, your partitions should be listed, click one and it will mount automatically and put an icon on the desktop.

---

### Post by Scootymad on 2009-02-25
> **Hobgoblin said:**
> Click on places, your partitions should be listed, click one and it will mount automatically and put an icon on the desktop.

The partitions are not listed on places :(

How do i run the commands with sudo?

---

### Post by chevmaro on 2009-02-25
> **Scootymad said:**
> The partitions are not listed on places :(

How do i run the commands with sudo?

In the terminal just type sudo in front of the commands.  It should ask for a password.

What drive setup do you have?  We know they are internal Sata.  What kind of partition is it?  NTFS or something?  You running raid?

---

### Post by Scootymad on 2009-02-25
> **chevmaro said:**
> In the terminal just type sudo in front of the commands.  It should ask for a password.

What drive setup do you have?  We know they are internal Sata.  What kind of partition is it?  NTFS or something?  You running raid?

The partitions are NTFS

---

### Post by fjgaude on 2009-02-25
Here you go:

Make a mountpoint:

```
sudo mkdir /home/ntfs
```

for example. Then run:

```
sudo fdisk -l
```

Notice the drive name for the ntfs drive. Then do this:

```
sudo mount -t ntfs /dev/sdc1 /home/ntfs
```

That should do it. Later you can have the drive mount automatically at boot time by placing a line in your **/etc/fstab** file.

Let us know if you undersand, how you are doing.

---

### Post by Scootymad on 2009-02-26
On the third code:

sudo mount -t ntfs /dev/sdc1 /home/ntfs

it tells me that it has failed to access volume

---

### Post by Scootymad on 2009-02-26
What does all this mean?

glenn@glenn-laptop:~$ sudo mount -t ntfs /dev/sdc1/home/ntfs
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by Slim Odds on 2009-02-26
> **Scootymad said:**
> What does all this mean?

glenn@glenn-laptop:~$ sudo mount -t ntfs /dev/sdc1/home/ntfs

It means that you forgot a space between the device name and the mount location

---

### Post by Scootymad on 2009-02-26
Right, sorted that but i have this error when i put it in correctly

ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

---

### Post by Slim Odds on 2009-02-26
> **Scootymad said:**
> Right, sorted that but i have this error when i put it in correctly

ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

Does```
sudo fdisk -l
```show a drive called /dev/sdc1?

---

### Post by Scootymad on 2009-02-26
> **Slim Odds said:**
> Does```
sudo fdisk -l
```show a drive called /dev/sdc1?

we have /dev/sda1        /dev/sda2            /dev/sda5

---

### Post by Slim Odds on 2009-02-26
> **Scootymad said:**
> we have /dev/sda1        /dev/sda2            /dev/sda5

Well, that would explain why it complained about /dev/sdc1

Which one is your NTFS partition?

---

### Post by Scootymad on 2009-02-26
> **Slim Odds said:**
> Well, that would explain why it complained about /dev/sdc1

Which one is your NTFS partition?

sda1 is the NTFS

---

### Post by Slim Odds on 2009-02-26
> **Scootymad said:**
> sda1 is the NTFS

OK, try replacing sdc1 with sda1

---

### Post by Scootymad on 2009-02-26
I have tried mounting all 3 that it has come up with and its saying none of them have a valid NTFS format.

How would I reformat one of them to NTFS

---

### Post by Wayne_V on 2009-02-27
Can you post the output of 'sudo fdisk -l' and 'mount'?   If you only have one disk with three partitions it sounds like you wiped it clean when you installed -- there may be no unused partition.

---

