---
title: "ntfs partition not mounted, or is it?"
date: 2009-05-03
forum: General Help
---

### Post by sanderj on 2009-05-03
Hi,

I have a problem with the (not) automatically mounting of a NTFS partition /dev/sda1 on /media/ntfs after booting:

After booting Ubuntu 9.04, the directory /media/ntfs is empty, but the OS says /dev/sda1 *is* mounted. Strange: it should then not be empty.

When I try to umount, the OS says the partition is *not* mounted. Even more strange.

Then after mounting it (again?), it is really mounted, and the content is visible.

In the GUI System -> Administration -> Partition Editor, it says the partition has flag 'boot'.

How can I solve this problem? I want the partition /dev/sda1 to be mounted automagically on /media/ntfs after a boot.


```


ubuntu@ubuntu:~$ dmesg | grep -i ntfs
ubuntu@ubuntu:~$ dmesg | grep -i sda
[    2.484250] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.484272] sd 0:0:0:0: [sda] Write Protect is off
[    2.484275] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.484309] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.484381] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.484400] sd 0:0:0:0: [sda] Write Protect is off
[    2.484403] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.484433] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.484438]  sda: sda1
[    2.493800] sd 0:0:0:0: [sda] Attached SCSI disk

ubuntu@ubuntu:~$ ls /media/ntfs/

ubuntu@ubuntu:~$ mount | grep sda
/dev/sda1 on /media/ntfs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

ubuntu@ubuntu:~$ grep -i sda /etc/fstab 

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/ntfs/
mount: according to mtab, /dev/sda1 is already mounted on /media/ntfs

ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/ntfs/
ubuntu@ubuntu:~$ ls /media/ntfs/
AUTOEXEC.BAT  Config.Msi              firefox-download  IO.SYS                 MSDOS.SYS     ntldr                          RECYCLER                   wbin
BOOT.BAK      CONFIG.SYS              Firefox-Profile  
<snip>
ubuntu@ubuntu:~$ 

```

---

### Post by ibuclaw on 2009-05-03
To automatically mount the filesystem during boot, you have to add it to your fstab listing. (from what you've given, it doesn't appear to be there unless you made a mistake in pasting).

```
sudo gedit /etc/fstab
```
And put in:
```
/dev/sda1       /media/ntfs    ntfs    users,gid=46,umask=007 0 0
```
Regards
Iain

---

### Post by sanderj on 2009-05-03
Thanks. I tried that, but after the reboot, /etc/fstab is 'clean' again. It seems /etc/fstab is overwritten at boot time. I must confess I use a USB stick with a live install + persistence installed onto it. I *can* save stuff (in normal places?), but maybe not in /etc/fstab?

To verify this, I will write something into /etc/ and see whether it's still there after reboot.


Here's the situation after reboot:
```

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

ubuntu@ubuntu:~$ ls -al /etc/fstab
-rw-r--r-- 1 root root 53 2009-05-03 23:13 /etc/fstab

ubuntu@ubuntu:~$ date
Sun May  3 23:15:21 UTC 2009
ubuntu@ubuntu:~$ uptime
 21:35:23 up 2 min,  8 users,  load average: 1.42, 0.82, 0.31
ubuntu@ubuntu:~$ 
```

---

### Post by sanderj on 2009-05-03
Well, newly created files in /etc/ are still there after a reboot. So that's no the explanation of the /etc/fstab clean-up after reboot ... :-(

---

### Post by kayvortex on 2009-05-03
I'm not sure about the details of how live install works exactly, especially with regards to /etc/fstab, but there a few dirty hacks you could make instead that come to mind (although, they might not work either). One is to add a mount command to System -> Preferences -> Sessions, and the other is adding a init script (more work required for that one!) or alternatively just editing /etc/init.d/rc.local (but I seem to remember trouble with getting that to work).

But, those aren't really proper solutions, so maybe it's worth taking a look into if you can tell the system to keep changes to fstab: like I said, I can't really help with that one. Still, a dirty hack is better than nothing at all in the short-term!

---

