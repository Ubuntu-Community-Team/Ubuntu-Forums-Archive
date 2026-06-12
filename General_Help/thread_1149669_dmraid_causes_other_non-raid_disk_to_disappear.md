---
title: "dmraid causes other non-raid disk to disappear"
date: 2009-05-05
forum: General Help
---

### Post by bman917 on 2009-05-05
**Problem:**
When I install dmraid, I'm able to activate and mount my raid disks, however the other non-raid disk disappears.

**Details:**
I have the following hard drives:
150GB VelociRaptor - The boot drive. This is where Ubuntu is installed
80GB - I have two 80GB disks. Not in raid
160GB - I have two 160GB disks that are setup in RAID.

**NOTE:**
For nvidia nforce 680i, a RAID array needs to be enabled on through the BIOS. I'm POSITIVE that RAID is only enabled for the two 160GB drives. RAID is NOT enabled on the two 80GB drives. Again, I'm 100% sure the problem is not BIOS related.

My main disk is setup as dual boot. When I boot using windows, all drives are detected. And so I'm sure there is no problem with either of the RAID disks or the non-raid disks.

**Devices before installing dmraid:**[INDENT]ls -l /dev/sd*

brw-rw---- 1 root disk 8,  0 2009-05-05 18:08 /dev/sda
brw-rw---- 1 root disk 8,  1 2009-05-05 18:08 /dev/sda1
brw-rw---- 1 root disk 8,  2 2009-05-05 18:08 /dev/sda2
brw-rw---- 1 root disk 8,  5 2009-05-05 16:08 /dev/sda5
brw-rw---- 1 root disk 8,  6 2009-05-05 18:08 /dev/sda6
brw-rw---- 1 root disk 8, 16 2009-05-05 18:08 /dev/sdb
brw-rw---- 1 root disk 8, 17 2009-05-05 18:08 /dev/sdb1
brw-rw---- 1 root disk 8, 18 2009-05-05 18:08 /dev/sdb2
brw-rw---- 1 root disk 8, 32 2009-05-05 18:08 /dev/sdc
brw-rw---- 1 root disk 8, 48 2009-05-05 18:08 /dev/sdd
brw-rw---- 1 root disk 8, 49 2009-05-05 18:08 /dev/sdd1
brw-rw---- 1 root disk 8, 64 2009-05-05 18:08 /dev/sde
brw-rw---- 1 root disk 8, 65 2009-05-05 18:08 /dev/sde1

[/INDENT]The sda* devices are the 150GB drive where ubntu is installed.
The sdb* and sdc* devices are the RAID devices.
The sdd* and sde* devices are non-RAID 80GB disks.

After installing dmraid, sde1 and sdd1 disappears. sde1 and sdd1 disappears even though fdisk tells me there still should be there:[INDENT]sudo fdisk -l

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c31e215

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f478d0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        9730    78148608    7  HPFS/NTFS

[/INDENT]Hare are the raid devices detected by dmraid:[INDENT]sudo dmraid -r

/dev/sde: nvidia, "nvidia_cededafd", stripe, ok, 156301486 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_cededafd", stripe, ok, 156301486 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_bfahfcfg", stripe, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_bfahfcfg", stripe, ok, 312581806 sectors, data@ 0
[/INDENT]Based on the number of sectors, the 160GB disks is the nvidia_bfahfcfg raid set. And it seems dmraid thinks that the 80GB disks are raid disks as well and dmraid identified is as nvidia_cededafd raid set.[INDENT]ls -l /dev/mapper
crw-rw---- 1 root root  10, 61 2009-05-05 18:08 control
brw-rw---- 1 root disk 252,  0 2009-05-05 16:59 nvidia_bfahfcfg
brw-rw---- 1 root disk 252,  3 2009-05-05 16:59 nvidia_bfahfcfg1
brw-rw---- 1 root disk 252,  4 2009-05-05 16:59 nvidia_bfahfcfg2
brw-rw---- 1 root disk 252,  1 2009-05-05 16:59 nvidia_cededafd
brw-rw---- 1 root disk 252,  2 2009-05-05 16:59 nvidia_cededafd1
[/INDENT]After installing dmraid, I'm able to mount the RAID disks:[INDENT]sudo mount -t ntfs /dev/mapper/nvidia_bfahfcfg1 /mnt/raid
[/INDENT]However, the devices /dev/sdd1 and /dev/sde1 (the partitions from the 80GB disks) disappears. I suspect that dmraid detected them as RAID disks and so added them to /dev/mapper. Mounting nvidia_cededafd or nvidia_cededafd1 does not work - they are not valid partitions.

Then I uninstall dmraid, /dev/sdd1 and /dev/sde1 comes back again and ubuntu is able to detect and mount them automatically for me. However, the raid disks are not automatically detected.

**Using mdadm**:
Using mdadm does not work too. I tried variouse way to 'assemble' my raid disks using mdadm - no success.

Please help :(

---

### Post by bman917 on 2009-05-05
I forgot to mention, I also tried deactivating the *nvidia_cededafd* raid set. *nvidia_cededafd *is the raid set comprised of the 80GB disks that dmraid detected as raid devices.

This did not help. The non-raid disks are still missing although the raid set with the 80GB disk are gone from /dev/mapper

sudo dmraid -r
/dev/sde: nvidia, "nvidia_cededafd", stripe, ok, 156301486 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_cededafd", stripe, ok, 156301486 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_bfahfcfg", stripe, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_bfahfcfg", stripe, ok, 312581806 sectors, data@ 0

sudo dmraid -an nvidia_cededafd

ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 61 2009-05-05 18:08 control
brw-rw---- 1 root disk 252,  0 2009-05-05 16:59 nvidia_bfahfcfg
brw-rw---- 1 root disk 252,  3 2009-05-05 16:59 nvidia_bfahfcfg1
brw-rw---- 1 root disk 252,  4 2009-05-05 16:59 nvidia_bfahfcfg2


ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2009-05-05 18:08 /dev/sda
brw-rw---- 1 root disk 8,  1 2009-05-05 18:08 /dev/sda1
brw-rw---- 1 root disk 8,  2 2009-05-05 18:08 /dev/sda2
brw-rw---- 1 root disk 8,  5 2009-05-05 16:08 /dev/sda5
brw-rw---- 1 root disk 8,  6 2009-05-05 18:08 /dev/sda6
brw-rw---- 1 root disk 8, 16 2009-05-05 18:08 /dev/sdb
brw-rw---- 1 root disk 8, 32 2009-05-05 18:08 /dev/sdc
brw-rw---- 1 root disk 8, 48 2009-05-05 18:08 /dev/sdd
brw-rw---- 1 root disk 8, 64 2009-05-05 18:08 /dev/sde

---

### Post by ronparent on 2009-05-05
Because of the multitude of raid schemes implemented on various mainstream mother boards, it is difficult to make specific comments here. You appear to have been pretty thourough in examining your own situation. With a little bit more information I might be able to offer some suggestions.

How are your various drives physically interfaced (ie ide, sata), and which are located where? How many interfaces of each type are on the motherboard? Whose are the raid bios's (nVidia, sil, imicron, etc.) spanning which drive ports. Your situation seems particularly challanging.

---

### Post by bman917 on 2009-05-06
Hi ronparent, 

Thanks for taking interest on my dilema. Here are answeres to your questions

1. How are your various drives physically interfaced (ie ide, sata), and which are located where?

    All of my drives interface is SATA.


2. Whose are the raid bios's (nVidia, sil, imicron, etc.) spanning which drive ports.

[INDENT]RAID bios is nVidia. 
My motherboard is nVidia nforce 680i.
On my BIOS setting SATA ports 3 and 4 are RAID enabled and these corresponds to the following devices: /dev/sdb and /dev/sdc
[/INDENT]
3. Info on my RAID scheme:

My RAID scheme is RAID0 (stripping) using the default 64KB block size.


PS: I'm able to mount my raid volume. My problem is the non-raid disk disappears as soon as I install dmraid. So I'm thinking maybe there's a secret setting so that I can specifically tell dmraid not to touch my non-raid disks. Or perhaps there's an alternative way (other than dmraid) of mounting my RAID disk.

I've already tried (and failed) using mdadm. Here are my attempts:

>sudo mdadm --assemble --scan
mdadm: No arrays found in config file or automatically

> sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc
mdadm: no recogniseable superblock on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted

> sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc
mdadm: no recogniseable superblock on /dev/sdb1
mdadm: /dev/sdb1 has no superblock - assembly aborted

> sudo mdadm --assemble /dev/md0 /dev/sdb2 /dev/sdc
mdadm: no recogniseable superblock on /dev/sdb2
mdadm: /dev/sdb2 has no superblock - assembly aborted

> sudo mdadm --assemble /dev/md0 /dev/sdbc
mdadm: cannot open device /dev/sdbc: No such file or directory
mdadm: /dev/sdbc has no superblock - assembly aborted

---

### Post by ronparent on 2009-05-06
I believe that what is happening is that the 80 Gb drives had, at one time, been assembled into a raid device. This being the case, it also appears tha the so called metadata for the that raid was not erased when raid was deactivated in bios for those drives. If that is the case then the following instructions from **man dmraid** would apply.

              If  -E is added to -r the RAID metadata on the devices gets con&#8208;
              ditionally erased.  Useful to erase old metadata after  new  one
              of  different type has been stored on a device in order to avoid
              discovering both. If you enter -E option -D will be enforced  in
              order  to have a fallback in case the wrong metadata got erased.
              Manual copying back onto the device is needed  to  recover  from
              erasing  the  wrong  metadata  using  the  dumped  files device&#8208;
              name_formatname.dat and  devicename_formatname.offset.   Eg,  to
              restore  all *.dat files in the working directory to the respec&#8208;
              tive devices:

Since you do not want those drives recognized as raid, it appears that this should clear up your problem, I apologize if I am not being completely coherent, since flu is muddling up my ablity to think clearly.

---

### Post by bman917 on 2009-05-07
ronparent, I didn't know you have psychic powers!

Yes, you're absolutely correct, those old 80GB disks used to have been assembled into a raid device.

Indeed using -E to delete the meta data is the solution!!! After deleting the meta-data, dmraid now only detects the correct raid device.

Problem solved. Thanks very much master ronparent!

---

### Post by ronparent on 2009-05-07
Your most welcome. Glad I could help.

---

