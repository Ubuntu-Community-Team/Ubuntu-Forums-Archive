---
title: "swap partition is missing"
date: 2012-11-16
forum: Desktop Environments
---

### Post by zobayer1 on 2012-11-16
Hello, I am not sure if this is the appropriate place to post this, looks like proper section to me.
I am currently using Ubuntu 12.04 precise x64 version. I have two hard drive on my machine, one is for windows (in ntfs system) and the other is for linux (ext4). When I freshly installed 12.04 few months ago, I put around 15GB swap space (2x the size of the RAM).

I usually get an warning at the boot screen saying that /dev/mapper/cryptswap1 is not yet ready or present. Haven't dig through it before, but today, after searching the forum related to this, but then I've found mine is not quite similar case.

So, I ran a few test on the terminal and here are the outputs:
```

zobayer@precise:~$ sudo mount -l
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb5 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/zobayer/.Private on /home/zobayer type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=4b0c754e86f0af87,ecryptfs_fnek_sig=d19c7d0f9ce74024)
gvfs-fuse-daemon on /home/zobayer/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zobayer)
zobayer@precise:~$ 

```

Also, this is in my fstab file:
```

zobayer@precise:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=af89c49c-7fec-4730-8402-14de941d1d91 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=7991773d-c24b-444e-95ef-a763b5c3b665 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
#UUID=6cc3a988-bf1e-4206-b54f-5de83320786b none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
zobayer@precise:~$

```

It says swap was allocated during installation, so where has it gone now?

Then I use blkid to see the drives and swap is not loaded there
```

zobayer@precise:~$ sudo blkid
/dev/sda1: LABEL="Windows" UUID="387CB19B7CB1547A" TYPE="ntfs" 
/dev/sda5: LABEL="Media" UUID="F2A0E5F2A0E5BCEB" TYPE="ntfs" 
/dev/sda6: LABEL="Games" UUID="2EBCEBAFBCEB702F" TYPE="ntfs" 
/dev/sda7: LABEL="Work" UUID="62F4F8A0F4F8779D" TYPE="ntfs" 
/dev/sda8: LABEL="Music" UUID="E278FE1778FDEA65" TYPE="ntfs" 
/dev/sdb1: UUID="af89c49c-7fec-4730-8402-14de941d1d91" TYPE="ext4" 
/dev/sdb5: UUID="7991773d-c24b-444e-95ef-a763b5c3b665" TYPE="ext4" 
zobayer@precise:~$

```

Here sda is the drive used by windows system, and sdb is for linux. And swap is not there.

So I checked system monitor, it also shows only the / and /home which are 75GB each. It also says Swap is not available (below the memory usage charts).

Also Disk Utility program shows that 15 GB is of Unknown format, although it tells the type is Linux Swap 0x82.

It is not that the performance is degrading, still I think swap should be needed. How can I get rid of the boot screen warning about cryptswap1 not being loaded and also loading the swap partition, cause 15 GB is quite a lot amount to be left unnoticed.

Should I delete the partition and recreate it? also during re-creation, should I make it as bootable?

Thanks in advance.

---

### Post by oldfred on 2012-11-16
Swap gets converted to encrypted when you encrypt /home. Then gparted and some other tools do not really see swap, but partition table will still show it as swap. 
But if it is not getting mounted then it may have an issue. 

I have not used encryption so I do not know for sure what swap does look like. There was an issue where some partitions were not getting UUIDs, but I do not know if encrypting it then means tools like blkid cannot open partition or not.

Not sure this even applies with just an encrypted /home.
       Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

---

### Post by zobayer1 on 2012-11-17
Hi, thanks for the quick response as usual, yes I have encrypted my /home directory and after doing some experiment, I got the swap space back. I basically created a new swap on sdb6 with this:
```

sudo swapoff -a
sudo mkswap /dev/sda6
sudo swapon /dev/sda6
sudo ecryptfs-setup-swap

```However, the last command did not work as expected, even it tried to check sda6 even when I mentioned sdb6 which almost took my breath away. However, it was able to fix the cryptswap1 warning, and also now System Monitor shows 13.7 GB as swap (as expected). Disk Utility still finds this as unknown with type Linux Swap 0x82.

After doing this, the output of blkid looks like this:
```

zobayer@precise:~$ sudo blkid
[sudo] password for zobayer: 
/dev/sda1: LABEL="Windows" UUID="387CB19B7CB1547A" TYPE="ntfs" 
/dev/sda5: LABEL="Media" UUID="F2A0E5F2A0E5BCEB" TYPE="ntfs" 
/dev/sda6: LABEL="Games" UUID="2EBCEBAFBCEB702F" TYPE="ntfs" 
/dev/sda7: LABEL="Work" UUID="62F4F8A0F4F8779D" TYPE="ntfs" 
/dev/sda8: LABEL="Music" UUID="E278FE1778FDEA65" TYPE="ntfs" 
/dev/sdb1: UUID="af89c49c-7fec-4730-8402-14de941d1d91" TYPE="ext4" 
/dev/sdb5: UUID="7991773d-c24b-444e-95ef-a763b5c3b665" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="a77c8a98-11eb-47bb-a328-bc17e939b40e" TYPE="swap" 
zobayer@precise:~$ 

```So I think it managed to get it's UUID properly as you have mentioned. So I think the problem is solved for now. Am I correct?

---

### Post by oldfred on 2012-11-17
If not getting any errors it seems like it is ok.

Seems like a large swap? Only if you have that much RAM and want to hibernate.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by zobayer1 on 2012-11-17
I already have 8GB ram and I was planning to get 8GB more when I installed it. So I put around 15GB in total in swap. But now it seems huge, but I don't want to break the partitions now anyway.

---

