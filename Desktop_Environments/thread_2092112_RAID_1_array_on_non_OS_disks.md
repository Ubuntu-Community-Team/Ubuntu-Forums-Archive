---
title: "RAID 1 array on non OS disks"
date: 2012-12-06
forum: Desktop Environments
---

### Post by skunkarific on 2012-12-06
I have looked all over for an answer to this.

I created a RAID1 array on two non OS 3TB GPT disks using mdadm, it built, formatted EXT3, shows up in "Computer" as raidarray: DATA. Won't open. I have also tried 
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf which returns:
bash: /etc/mdadm/mdadm.conf: Permission denied

When I type 
sudo mdadm --assemble md127p1

I get
sudo mdadm --assemble md127p1
sudo: unable to resolve host CHUX-OFFICE
mdadm: Unknown keyword automatically
mdadm: Unknown keyword devices=/dev/sda,/dev/sdc
mdadm: md127p1 not identified in config file.

Here is my config file:
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
devices=/dev/sda,/dev/sdc

# This file was auto-generated on Wed, 05 Dec 2012 14:34:04 -0500
# by mkconf $Id$
ARRAY /dev/md/CHUX-OFFICE:raidarray metadata=1.2 name=CHUX-OFFICE:raidarray UUID=e914546a:acda8d4c:18876044:5d3291b5


I'm missing something. Just don't know what I don't know.


When I typesudo mdadm --detail --scan >> /etc/mdadm.conf
I get
bash: /etc/mdadm.conf: Permission denied

When I type (in terminal) mount /dev/md127 I get:
mount: can't find /dev/md127 in /etc/fstab or /etc/mtab

Here is the output of blkid:

/dev/sda: UUID="e914546a-acda-8d4c-1887-60445d3291b5" UUID_SUB="09db3d27-f028-d46e-2c4f-e5b9b33e9ac8" LABEL="CHUX-OFFICE:raidarray" TYPE="linux_raid_member" 
/dev/sdb1: UUID="b0356e31-e000-4e2b-8686-692f4903ac75" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: TYPE="swap" 
/dev/sdb3: LABEL="data" UUID="758b15ec-6cbe-4e66-ace9-4b21275987c6" TYPE="ext3" 
/dev/sdb4: LABEL="home" UUID="eae4f52b-4871-4285-8abd-dbf46da85eaa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc: UUID="e914546a-acda-8d4c-1887-60445d3291b5" UUID_SUB="341a001c-d676-b582-722a-12243a52ff87" LABEL="CHUX-OFFICE:raidarray" TYPE="linux_raid_member"

Here is my fstab file:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=b0356e31-e000-4e2b-8686-692f4903ac75 / ext3 errors=remount-ro 0 1
# /home was on /dev/sda3 during installation
UUID=eae4f52b-4871-4285-8abd-dbf46da85eaa /home ext3 defaults 0 2
# swap was on /dev/sda2 during installation
UUID=3e13c3de-2af0-43ee-a480-330114bbe11d none swap sw 0 0

---

