---
title: "mke2fs hangs when formatting larger disks"
date: 2009-03-18
forum: General Help
---

### Post by jrx1 on 2009-03-18
Hi!

I'm running Ubuntu server 8.04 LTS, all commands are made in
xen dom0 while several guests are running.
I have just updated my system with
> apt-get upgrade && apt-get dist-upgrade

> uname -a
Linux server3 2.6.24-23-xen #1 SMP Mon Jan 26 03:12:59 UTC 2009 i686 GNU/Linux

The problem is that system hangs when I'm creating new xen guests. And I have located the problem to the command which is causing it - mke2fs.

So I manually run this command and it hanged while formatting 200GB disk, it completed OK with 100GB disk.

----------------------------------------------------------------
root@server3:~# lvcreate raid5 -L 200Gb -n test-disk
  Logical volume "test-disk" created

root@server3:~# mkfs.ext3 -F /dev/raid5/test-disk
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
13107200 inodes, 52428800 blocks
2621440 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1600 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables:  513/1600
----------------------------------------------------------------

After that server must be switched off because I could not reboot it.

Here is output from fstab:
----------------------------------------------------------------
root@server3:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/raid5-dom0
UUID=6d681eaf-2eec-459e-8439-eda991db7e50 /               ext3    relatime,errors=remount-ro 0       1
# /dev/md0
UUID=f36b324b-d9d6-4d48-beee-bc80cf1843e5 /boot           ext3    relatime        0       2
# /dev/mapper/raid5-dom0_swap
UUID=9eb16227-7c05-45e1-91d3-86c8ea376dc1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
----------------------------------------------------------------

The server has 8GB RAM and
Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.40GHz
processor.

If you need any additional information please let me know.

Any help would be highly appreciated.

Jurgis

---

### Post by jrx1 on 2009-03-18
Sugestion in this article
[http://www.mailinglistarchive.com/ext3-users@redhat.com/msg00999.html]("http://www.mailinglistarchive.com/ext3-users@redhat.com/msg00999.html")
solved the problem.

I added this line
**export MKE2FS_SYNC=10**
to my .bashrc file and it worked

---

