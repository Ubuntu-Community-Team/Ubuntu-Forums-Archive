---
title: "Help: Making Clone Partition Bootable"
date: 2009-02-21
forum: General Help
---

### Post by ladymc on 2009-02-21
Hello all,

I followed the tutorial [here]("http://ubuntuforums.org/showthread.php?t=470623") to clone my linux partition to another hard drive.

Problem is after running the copy (cp -a *) successfully, I'm unable to make to partition bootable.

Some info first

**Clone : /dev/sdb7 -> /dev/sda6**

sudo blkid

[I]/dev/sda1: UUID="DCA0652EA0651076" LABEL="Windows 7" TYPE="ntfs" 
/dev/sda5: UUID="cf335fa5-136b-48e3-b56d-3ed6039506f8" TYPE="swap" 
/dev/sda6: UUID="95978c58-699c-4e87-9253-edd02f2cc32c" TYPE="ext3" 
/dev/sda7: UUID="FE940D8E940D4B1B" LABEL="NewData" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
[/I]


Here's what I've tried and the result

ubuntu@ubuntu:~$ sudo chroot /tmp/sda6
root@ubuntu:/# grub-install hd0
*/dev/sdb7: Not found or not a block device.*

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/tmp/sda6 hd0
*The file /tmp/sda6/boot/grub/stage1 not read correctly.*

ubuntu@ubuntu:~$ sudo grub --boot-drive=/dev/sda6
grub> find /boot/grub/stage1
*Error 15: File not found*

and when I try to boot from the drive the Grub loader returns *"Error 21"*


Tried modifying the menu.lst and /etc/fstab as well

For menu.lst I changed the root value from (hd0,6) to (hd0,5) as below. And in the kernel value I set 'root=/dev/sda6', before it had UUID value for /dev/sdb7 (original/source partition)

=============menu.lst=============

#title		     Ubuntu 8.04.1, kernel 2.6.24-22-generic
title		     Hardy Heron
root		     (hd0,5)
kernel		     /boot/vmlinuz-2.6.24-22-generic root=/dev/sda6 ro quiet splash
initrd		     /boot/initrd.img-2.6.24-22-generic
quiet

title		     Windows 7
root		     (hd0,0)savedefault 
makeactive
chainloader	     +1
-----------------


For fstab all I changed were the UUIDs from the source values to the new destination values.

=============/etc/fstab=============

# /dev/sda6
UUID=95978c58-699c-4e87-9253-edd02f2cc32c /    ext3    relatime,errors=remount-ro 0       1

# /dev/sda5
UUID=cf335fa5-136b-48e3-b56d-3ed6039506f8 none swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0      

# /dev/sda7
UUID=FE940D8E940D4B1B 	/media/NewData	ntfs users,defaults,umask=000 0 0 
-------------------



Please help. I am familiar with ubuntu but I'm still a bit noobish, so kindly save me from myself ;)

Thank you

---

### Post by dcstar on 2009-02-21
> **ladymc said:**
> Hello all,

I followed the tutorial [here]("http://ubuntuforums.org/showthread.php?t=470623") to clone my linux partition to another hard drive.

Problem is after running the copy (cp -a *) successfully, I'm unable to make to partition bootable.

Some info first

**Clone : /dev/sdb7 -> /dev/sda6**
..........

"Cloning" a partition is a simple procedure that the Partition Editor can do without requiring a ridiculous quantity of commands in a terminal - simply copy and paste the partition - the UUID will remain the same.

If you want to boot off the partition then all that is required is to install Grub onto it **and** modify the /boot/grub/menu.lst file on the copied partition to reflect the new drive parameters (and any other partitions on the drive).

As that "tutorial" says (change the **highlighted** values as required):
-------
Note: If you need to install Grub, boot the Ubuntu CDROM, click on the Terminal, to get a shell prompt.

```
sudo grub
grub> find /boot/grub/stage1* <-- find all Linux partitions*
grub> root (hd**1,2**)* <-- select the partition that has /boot/grub/menu.lst*
grub> setup (**hd0**)* <-- drive that boots – usually hd0*
grub> quit
```

---

### Post by ladymc on 2009-02-21
That's fantastic advice, except for the fact that I did that and I'm still here asking for help.

Since you can't help with my present problem, I'll just look into using Partition Editor.

Thanx anyways

Anybody else can assist before I waste time trying another cloning method. I just need to get it to boot and the ways I know of aren't working.

---

### Post by ladymc on 2009-02-22
I just noticed that Partition Editor has the partition listed as ext3 as it should be, but fdisk is showing both it and the swap as fat16.

I formatted using Partition Editor... the swap I did using mkswap.

Can someone please help me.

---

### Post by ladymc on 2009-02-23
Admins, 

Feel free to delete/close this thread. Gave up and reinstalled.

Thanx

---

