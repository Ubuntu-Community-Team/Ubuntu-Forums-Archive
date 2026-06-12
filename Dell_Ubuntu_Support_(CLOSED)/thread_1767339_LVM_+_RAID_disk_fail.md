---
title: "LVM + RAID disk fail"
date: 2011-05-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ubazeno on 2011-05-25
I'm trying to recover from a disk replacement in a PowerEdge 2850.  It (was) running Ubuntu 10.10.

We have a Raid 1 with two disks and a Raid 5 with four.  One of the Raid 5 disks failed while a service tech was swapping parts around troubleshooting another problem (system hangs during SCSI scan on every-other boot, which is still a problem and is apparently a different disk than the one that failed).  Anyway, the failed disk was replaced and appears online in the Ctl-M / U827 utility.  

The problem is that LVM cant find /root.  /boot and swap were created in their own partitions on the Raid 1, then the remaining space and the entire Raid 5 were brought into LVM.  I can't seem to access any of the filesystem through manual means.  

From the Grub prompt an ls -l shows all 8 of the filesystem folders (vg0-root, vg0-usr, etc.) but I can't ls the file systems as expected, ie ls -l (vg0-root)/.  I can ls -l (hd0,msdos1)/ and see the boot files, grub directory, etc.  Also, when I ls -l at grub> all the vg0-... show Unknown filesystem.  I don't know if that's normal because LVM was managing that space or not.  

Also, if I boot to my gParted Live CD the partition editor shows the Raid 5 as "Unallocated".  

I've done some things trying to edit the grub file to hit a different uuid.  Initially, the pvdisplay, pvscan, etc. were all reporting that uuid Fesd.... could not be found, and I found a vg0_xxxx.vg file with an empty PV Name and a Flag of ["MISSING"] for an entry corresponding to the UUID.  So I added /dev/sdb (simulating the partition of the other entry that seems good /dev/sda1), removed "MISSING" and ran pvcreate -uuid .... -restorefile vg0_xxxx.vg /dev/sdb   This action stopped the not found error but I still cant access the file system.  

Is the uuid wrong? can I somehow probe the Raid 5 for an internal id to use? Is the Raid 5 wiped, corrupted? Is there some way to restore it? 

Any assistance is appreciated!

---

### Post by psusi on 2011-05-25
Is this a fakeraid or software raid?  Does gparted see /dev/md0, or /dev/mapper/something?

---

### Post by ubazeno on 2011-05-25
No its a Perc 4e/Di hardware controller.  gParted sees /dev/sdb as unallocated.  The Raid 1 LVM partition shows up as /dev/sda5.  

Any ideas?

---

### Post by ubazeno on 2011-05-25
I have also tried to boot manually at the grub> prompt by 

```

set prefix=(hd0,msdos1)
set root=(hd0,msdos1)

and several other variations...
root=(hd0,msdos1)/
root=(hd1,vg0-root)
root=(vg0-root) ....

linux /vmlinuz /dev/sdb, etc 


```but I don't really expect any of these to work with the ls -l listing "Unknown Filesystem".  Its as if LVM isn't starting or cant figure where anything is, or that there's something wrong with the array itself, as in empty.  

If I boot to the gParted disk and do a pvscan it shows the two PV's, one being /dev/sda5 and the other being the /dev/sdb that I named in the pvcreate command mentioned before.  

If it helps, here are results of a few commands when booted to the live cd:

blkid:
```

/dev/sda1: LABEL="boot" UUID="6b2af607-4c93-47e8-bd26-53b0125f1b4d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="3a8eefed-d137-45b1-b5c5-8b7749671d0e" TYPE="swap" 
/dev/sda5: UUID="09Mqic-CqmJ-E16I-SRQ7-2G3q-Yf3k-7OhJdc" TYPE="LVM2_member" 
/dev/sdb: UUID="Fesdv8-D50V-mGIc-Aujd-qTmH-ozJJ-OkvGQR" TYPE="LVM2_member" 

```lvdisplay:
```

  --- Logical volume ---
  LV Name                /dev/vg0/root
  VG Name                vg0
  LV UUID                TXygMg-6Ycv-ujOH-FyXd-IMYB-45Kd-IEKZVu
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                27.94 GiB
  Current LE             7152
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:0
   
  --- Logical volume ---
  LV Name                /dev/vg0/tmp
  VG Name                vg0
  LV UUID                VNLquz-Ta5P-P4se-wazN-M9Nj-Fjrz-grdHHI
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                952.00 MiB
  Current LE             238
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:1
   
  --- Logical volume ---
  LV Name                /dev/vg0/usr
  VG Name                vg0
  LV UUID                fA5N7u-WW9a-AWrX-79Db-JhOG-QaiI-qg6G2A
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                2.79 GiB
  Current LE             715
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:2
   
  --- Logical volume ---
  LV Name                /dev/vg0/var
  VG Name                vg0
  LV UUID                GTcmYE-atzF-k8dd-kSAl-hUQn-ZcI3-6eVeEs
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                27.94 GiB
  Current LE             7152
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:3
   
  --- Logical volume ---
  LV Name                /dev/vg0/home
  VG Name                vg0
  LV UUID                DrnOLF-F0tk-kEHC-S7Zl-MAfQ-LWjv-iYKCFV
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                2.79 GiB
  Current LE             715
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:4
   
  --- Logical volume ---
  LV Name                /dev/vg0/opt
  VG Name                vg0
  LV UUID                kjvewJ-kkXa-qUfh-EmJ7-KHkg-HxOW-N9pLyh
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                139.70 GiB
  Current LE             35762
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:5
   
  --- Logical volume ---
  LV Name                /dev/vg0/u1
  VG Name                vg0
  LV UUID                erO0t7-j8ou-HFaY-Clcl-wJcA-n232-cuK22T
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                74.50 GiB
  Current LE             19073
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:6
   
  --- Logical volume ---
  LV Name                /dev/vg0/u2
  VG Name                vg0
  LV UUID                51hcVm-DQ63-fHVF-1akd-tZp2-QGaQ-UvUOMH
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                74.50 GiB
  Current LE             19073
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:7
   

```pvdisplay:
```

  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               vg0
  PV Size               132.68 GiB / not usable 1.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              33966
  Free PE               33966
  Allocated PE          0
  PV UUID               09Mqic-CqmJ-E16I-SRQ7-2G3q-Yf3k-7OhJdc
   
  --- Physical volume ---
  PV Name               /dev/sdb
  VG Name               vg0
  PV Size               409.86 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              104924
  Free PE               15044
  Allocated PE          89880
  PV UUID               Fesdv8-D50V-mGIc-Aujd-qTmH-ozJJ-OkvGQR
   

```dmsetup table:
```

vg0-u1: 0 156246016 linear 8:16 423805312
vg0-opt: 0 292962304 linear 8:16 130843008
vg0-home: 0 5857280 linear 8:16 124985728
vg0-tmp: 0 1949696 linear 8:16 58589568
vg0-root: 0 58589184 linear 8:16 384
vg0-usr: 0 5857280 linear 8:16 60539264
vg0-var: 0 58589184 linear 8:16 66396544
vg0-u2: 0 156246016 linear 8:16 580051328

```dmsetup ls:
```
vg0-u1    (251, 6)
vg0-opt    (251, 5)
vg0-home    (251, 4)
vg0-tmp    (251, 1)
vg0-root    (251, 0)
vg0-usr    (251, 2)
vg0-var    (251, 3)
vg0-u2    (251, 7)

```dmsetup status:
```
vg0-u1: 0 156246016 linear 
vg0-opt: 0 292962304 linear 
vg0-home: 0 5857280 linear 
vg0-tmp: 0 1949696 linear 
vg0-root: 0 58589184 linear 
vg0-usr: 0 5857280 linear 
vg0-var: 0 58589184 linear 
vg0-u2: 0 156246016 linear 

```Can anyone say what the source of the pvscan and pvdisplay output is, whether its a file table of information maybe in /boot that IS accessible, or give a good idea of how to check that the raid still has the data?

---

### Post by psusi on 2011-05-25
That all looks good.  Try mounting the filesystems and see if your files are there.

---

### Post by ubazeno on 2011-05-26
I should've been clearer, but when I said in my first post that "LVM can't find /root" and " I can't seem to access any of the filesystem through manual means", I meant I can't mount them.  

If I try to 
```

mount /dev/sdb /mnt/sdb

or 

mount /dev/sda5 /mnt/sda

```
I get 'unknown filesystem "LVM2_member"'.  Is there a trick to this? Should I specify a file system type and which for LVM?  

Are there any LVM experts that can give quick Yes/No tests for 'can it be saved'?  I am faced with wiping it and rebuilding it Today, if it can't be fixed.

---

### Post by ubazeno on 2011-05-26
If I try to mount the LV like so:
```

mount -t ext2 /dev/vg0/root /mnt/sdb
# (or ext3)

```
I get this message:
> wrong fs type, bad option, bad superblock on /dev/mapper/vg0-root, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail or so

doing dmesg | tail the filesystem ext2 or ext3 is not found and it recommends running e2fsck.  Doing so shows the same basic problem, bad magic number in superblock... try an alternate superblock.

---

### Post by psusi on 2011-05-26
Were you using the ext3 filesystem on those volumes?  What does sudo blkid show?

---

### Post by ubazeno on 2011-05-26
blkid output is shown above.  Yes, I believe it was ext2 or 3.

---

### Post by psusi on 2011-05-26
Blkid didn't mention any of the logical volumes.  Did you run it before activating them?

---

### Post by ubazeno on 2011-05-26
The blkid listing shown above indicates the logical devices on the lines with Type="LVM2_member".  I also cleared the blkid cache and ran a low level blkid -p that shows the same results, with a couple of extra tags including USAGE="raid"...  

All 8 logical volumes are active, as seen with "dmsetup info" or "sudo lvm lvscan".

---

### Post by psusi on 2011-05-26
> **ubazeno said:**
> The blkid listing shown above indicates the logical devices on the lines with Type="LVM2_member".

No, that is the physical volume.  The logical volumes are the ones in /dev/mapper.

---

### Post by ubazeno on 2011-05-26
> What does sudo blkid show?```

/dev/sda1: LABEL="boot" UUID="6b2af607-4c93-47e8-bd26-53b0125f1b4d" SEC_TYPE="ext2" TYPE="ext3"  
/dev/sda2: UUID="3a8eefed-d137-45b1-b5c5-8b7749671d0e" TYPE="swap"  
/dev/sda5: UUID="09Mqic-CqmJ-E16I-SRQ7-2G3q-Yf3k-7OhJdc" TYPE="LVM2_member"  
/dev/sdb: UUID="Fesdv8-D50V-mGIc-Aujd-qTmH-ozJJ-OkvGQR" TYPE="LVM2_member"
```

---

### Post by ubazeno on 2011-05-26
If you're looking for this it is lvscan:

```

  ACTIVE            '/dev/vg0/root' [27.94 GiB] inherit
  ACTIVE            '/dev/vg0/tmp' [952.00 MiB] inherit
  ACTIVE            '/dev/vg0/usr' [2.79 GiB] inherit
  ACTIVE            '/dev/vg0/var' [27.94 GiB] inherit
  ACTIVE            '/dev/vg0/home' [2.79 GiB] inherit
  ACTIVE            '/dev/vg0/opt' [139.70 GiB] inherit
  ACTIVE            '/dev/vg0/u1' [74.50 GiB] inherit
  ACTIVE            '/dev/vg0/u2' [74.50 GiB] inherit

```

---

### Post by psusi on 2011-05-26
How about sudo blkid -p /dev/vg0/root?

---

### Post by ubazeno on 2011-05-26
Thanks for your replies.  The 
```

blkid -p /dev/vg0/root

```
doesn't return anything, just right back to the prompt.  If I run just
```

blkid -p 

```
I get a slightly expanded version of blkid that includes VERSION="LVM2 001" and USAGE="raid".  Aside from those two tags the output is identical to the listing earlier.  

I don't understand how the file system can appear to be there with the LVM tools but not be accessible.  Do these LVM tools pull the information from files it maintains or are they actually querying the disks and finding the metadata that's displayed?  When I try to 
```

mount /dev/vg0/root /mnt

```
why does it ask for a file system type and when supplied what is the "bad superblock" message telling me and is there a work around?

---

### Post by psusi on 2011-05-26
LVM just keeps track of volumes; whether a volume contains a filesystem is another matter.

Are you sure /dev/sdb is correct?  Normally you create an LVM partition to use as the PV.  If you originally did that, and then used sdb instead of sdb1 when you recreated the PV, that could explain it.

---

### Post by ubazeno on 2011-05-26
I've wondered the same thing, if "/dev/sdb" is correct?  As I mentioned originally, the pv device name tag in the vg0_xxxx.vg file was blanked and the volume was initially flagged missing.  All of the lvm tools were reporting that the device with uuid Fesd.... didn't exist.  I took a stab at it with "/dev/sdb", not knowing for sure if there was a partition on the device.  

So, what would the below vg file look like if there was a partition spanning the raid 5?

```

...   ...   ...  

vg0 {
    id = "be9nQc-jndX-Azxk-Wn5E-9rvx-t0UA-z39AUi"
    seqno = 11
    status = ["RESIZEABLE", "READ", "WRITE"]
    flags = []
    extent_size = 8192        # 4 Megabytes
    max_lv = 0
    max_pv = 0
    metadata_copies = 0

    physical_volumes {

        pv0 {
            id = "09Mqic-CqmJ-E16I-SRQ7-2G3q-Yf3k-7OhJdc"
            device = "/dev/sda5"    # Hint only

            status = ["ALLOCATABLE"]
            flags = []
            dev_size = 278251520    # 132.681 Gigabytes
            pe_start = 384
            pe_count = 33966    # 132.68 Gigabytes
        }

        pv1 {
            id = "Fesdv8-D50V-mGIc-Aujd-qTmH-ozJJ-OkvGQR"    # this is the uuid reported missing by LVM tools pvscan, etc.

            device = "/dev/sdb"    # Supplied "/dev/sdb" for device which was empty

            status = ["ALLOCATABLE"]
            flags = []                   # Removed "MISSING" from brackets
            dev_size = 859541504    # 409.861 Gigabytes
            pe_start = 384
            pe_count = 104924    # 409.859 Gigabytes
        }
    }

    logical_volumes {

        root {                    ...   ...   ...   

```

This .vg file was probably created by the gParted boot process.  The original .vg file backups should be in /etc/lvm/backups - which I can't access.  This could be the whole problem, but its the only file I have to use with pvcreate to recreate pv1.

---

### Post by psusi on 2011-05-26
Presumably sdb1.

---

### Post by ubazeno on 2011-05-27
Thanks.  I had tried that. It gave me a does not exist error.  

I'm currently wiping and rebuilding the system, but I know a disk is going to be replaced in the near future and I still don't know why this happened.

I didn't see anything that I did wrong in all of this.  The service tech replaced the disk when the power was off vs hot swap but the raid seemed to repair itself just fine.  On first boot I had the error that the device with UUID Fesdv8-.... was unknown.  

What precautions should I have taken?

---

### Post by psusi on 2011-05-27
Go through a disaster recovery drill this time to simulate such a failure and make sure you are familiar with how to recover for next time.

---

