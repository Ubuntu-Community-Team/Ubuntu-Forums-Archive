---
title: "GRUB Error 17 on power-up. Anyone know how I can modify a file on my laptop?"
date: 2008-12-22
forum: General Help
---

### Post by maphco on 2008-12-22
When I turn on my laptop I get this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17



Before this happened I was modifying a file.  I think if I replace the file with the backup one I created I'll have my laptop back to working order. Does anyone know of a way that I can do this?

---

### Post by azmo35 on 2008-12-22
Hi,in my case when the error 17 appeared I used the command "e" to edit the grub bootloader and add this hd0.1,before ()ubuntu after (hd0.1)ubuntu,if this worked then you need edit your menu.1st i hope this give any help.

---

### Post by maphco on 2008-12-22
Perhaps that might help. If you could give me detailed instructions on exactly how to do that I would appreciate it. But first, if it's possible, I would like to try and just to replace the modified file with the backup. Hope you understand.

---

### Post by joehte on 2008-12-22
> **maphco said:**
> Perhaps that might help. If you could give me detailed instructions on exactly how to do that I would appreciate it. But first, if it's possible, I would like to try and just to replace the modified file with the backup. Hope you understand.

Boot from the Live CD, mount your hd, and copy the backup file back in place.

Something like:

cd /mnt
sudo mkdir myhd
sudo mount /dev/hda0 myhd

Just use the correct dev.

---

### Post by azmo35 on 2008-12-22
What file you change? For the boot is esc or tab you will see maybe underneath this commands "e" for edit "b" for boot go ahed and clic on "e" and you have this ()ubuntu click on "e" again you have ()ubuntu_ now move the blink corsor to (_) and add hd0.1,
(hd0.1)ubuntu click on"b" to boot if workes you have your instalation again.
Ps:for hd0.1,i presume you only have two partitions if you have more change 1 for the number that partition.

---

### Post by maphco on 2008-12-22
Do you know how I can find out which device it is I need to mount?  or would it be "sdb" since that's the partition I installed it on when I installed intrepid.

---

### Post by maphco on 2008-12-22
Alright, azmo, thanks.  I'll try your idea if joehte's doesn't work. His just seems less risky from what I see is all.

---

### Post by maphco on 2008-12-22
Alright, I teid it with the line "sudo mount /dev/sdb myhd".  I used the command "sudo fdisk -l" to get some info and that looks like the correct one.

However, I just tried it with the line "sudo mount /dev/sdb1 myhd" since my files and stuff are on partition one and it said "you must specify the filesystem type.

---

### Post by joehte on 2008-12-22
> **maphco said:**
> Alright, I teid it with the line "sudo mount /dev/sdb myhd".  I used the command "sudo fdisk -l" to get some info and that looks like the correct one.

However, I just tried it with the line "sudo mount /dev/sdb1 myhd" since my files and stuff are on partition one and it said "you must specify the filesystem type.

This typically means that it's not the correct partition. If it was your Linux partition mount would recognize it. Remember that partitions start from 0, so maybe the correct one is /dev/sdb0.

---

### Post by maphco on 2008-12-22
"special device /dev/sdb0 does not exist"

---

### Post by joehte on 2008-12-22
Yeah I remembered wrong. The listing given by fdisk should be valid as it is. If you have several prospective looking partitions I'd advice trying them all. What does fdisk -l give as the partition type to you? Is it "Linux"? Or something else? One thing that comes to my mind that if you are using LVM then it requires a bit more as the Live CD doesn't come with LVM support out of the box.

---

### Post by maphco on 2008-12-22
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         400     3212968+  83  Linux
/dev/sda2             401         979     4650817+  83  Linux
/dev/sda3             980         980        8032+   c  W95 FAT32 (LBA)
/dev/sda4             981         981        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e1a7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3757    30178071   83  Linux
/dev/sdb2            3758        3924     1341427+   5  Extended
/dev/sdb5            3758        3924     1341396   82  Linux swap / Solaris

Disk /dev/sdc: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         969     1953439+   6  FAT16


That's the output of fdisk -l

---

### Post by joehte on 2008-12-22
Judging by the output of your fdisk -l, mounting /dev/sdb1 should work.

Also mounting /dev/sda1 and /dev/sda2 should work. Unfortunately I have no idea why you're getting that error.

---

### Post by joehte on 2008-12-22
The only thing I can add is that you could try specifying the type of the filesystem, but this is a long shot:

sudo mount -t ext3 /dev/sdb1 myhd

(or ext2 if you're using that).

---

### Post by wieman01 on 2008-12-22
Chiming in... What partition does your root partition reside on?

Please also post the contents of:
> sudo cat /boot/grub/menu.lst 
I believe Grub is looking for the wrong root location.

_**EDIT:**_
You would have to boot from LiveCD to get that information.

---

### Post by maphco on 2008-12-22
It says I must specify the filesystem type when I enter "sudo mount /dev/sdb1 myhd" Do you know how I can find the filesystem type and how I would correctly enter this at the terminal?

---

### Post by maphco on 2008-12-22
joehte: I tried that, yah, didn't work :(

wieman01: cat: /boot/grub/menu.lst: No such file or directory.

---

### Post by wieman01 on 2008-12-22
> **maphco said:**
> joehte: I tried that, yah, didn't work :(

wieman01: cat: /boot/grub/menu.lst: No such file or directory.
Oops, then the file is gone!

What about the backup:
> sudo cat /boot/grub/menu.lst~
Note the ~.

If that one is missing too, then we probably need to reinstall Grub.

What partition does root reside on again?

---

### Post by Elfy on 2008-12-22
If you are completely unsure where you're root is installed try to mount all three linux partitions

```
sudo mkdir /mnt/tmp1 /mnt/tmp2 /mnt/tmp3
sudo mount -t ext3 /dev/sda1 /mnt/tmp1
sudo mount -t ext3 /dev/sda2 /mnt/tmp2
sudo mount -t ext3 /dev/sdb1 /mnt/tmp3
```

Then run these and post the results

```
ls /mnt/tmp1/boot/grub/me*
ls /mnt/tmp2/boot/grub/me*
ls /mnt/tmp3/boot/grub/me*
```

Then we can see where the menu list is likely to be.

Wondering aloud if this is another thread where root should be replaced by uuid

---

### Post by wieman01 on 2008-12-22
Good point, forestpixie.

---

### Post by maphco on 2008-12-22
wieman: again, it said no such file oor directory. Actually, when I click oon File System in the left hand column of Nautilus then go into /boot i don't see a GRUB folder

forestpixie:

To the first section of code you told me to execute here is the output:

ubuntu@ubuntu:~$ sudo mkdir /mnt/tmp1 /mnt/tmp2 /mnt/tmp3
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/tmp1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /mnt/tmp2
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 /mnt/tmp3
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

To the second set of cold you told me to execute:

ubuntu@ubuntu:~$ ls /mnt/tmp1/boot/grub/me*
ls: cannot access /mnt/tmp1/boot/grub/me*: No such file or directory
ubuntu@ubuntu:~$ ls /mnt/tmp2/boot/grub/me*
ls: cannot access /mnt/tmp2/boot/grub/me*: No such file or directory
ubuntu@ubuntu:~$ ls /mnt/tmp3/boot/grub/me*
ls: cannot access /mnt/tmp3/boot/grub/me*: No such file or directory

---

### Post by Elfy on 2008-12-22
Open the partion editor in system>admin - it should tell you what filtype sda1 and sdb1 actually are - ext2 or ext3

We know that your grub is on sdsa1 or sdb1 now anyway.

---

### Post by maphco on 2008-12-22
It says that sda1 is ext2

but for sdb1 (which is where I had installed my OS) it says unknown and in the partition column it has an orange triangle with an exclamation mark in it...

---

### Post by Elfy on 2008-12-22
```
sudo mount -t ext2 /dev/sda1 /mnt/tmp1
ls /mnt/tmp1/boot/grub/me*
```

The exclamation mark would to me suggest a problem - let's deal with one thing at a time.

---

### Post by maphco on 2008-12-22
I ran that and it returned "/mnt/tmp1/boot/grub/menu.lst"

I didn't think it mattered, and perhaps it still doesn't, but this is an eee pc 1000 I'm working with. When I installed the version of ubuntu I'm working with it left the modified Xandros on it. So I believe sda1 to contain that OS, and sdb1 to contain the ubuntu OS. Sorry for not mentioning this at the start, I didn't think it was relevent.

---

### Post by Elfy on 2008-12-22
Lets see what sda1 has then -

```
cat /mnt/tmp1/boot/grub/menu.lst
```

Post it here please and also the result of

```
df -h
```

---

### Post by maphco on 2008-12-22
First returned:

#
# Configured by Xandros Configuration system.
#
hiddenmenu
# default boot entry
default=0

# Boot automatically after 1 second.
timeout=0

# Fallback to Configure.
fallback=2

title Normal Boot
	root (0x80,0)
	kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1
	initrd /boot/initramfs-eeepc.img

title Perform Disk Scan
	root (0x80,0)
	kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y
	initrd /boot/initramfs-eeepc.img

title Restore Factory Settings
	root (0x80,0)
	kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y
	initrd /boot/initramfs-eeepc.img

Second returned:

df: `/lib/modules/2.6.27-7-generic/volatile': No such file or directory
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  104K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.9M  498M   1% /dev
tmpfs                 501M  132K  501M   1% /dev/shm
rootfs                501M   50M  451M  10% /
/dev/sdc1             1.9G  875M  1.1G  46% /cdrom
/dev/loop0            835M  835M     0 100% /rofs
tmpfs                 501M   16K  501M   1% /tmp
/dev/sda2             4.4G  945M  3.3G  23% /mnt/tmp2
/dev/sda1             3.1G  2.8G  259M  92% /mnt/tmp1

---

### Post by maphco on 2008-12-22
How can I format the second part better so it'll be more readble for you two?

---

### Post by Elfy on 2008-12-22
Yep - that means little to me ;)

You can use gparted to try and see what's going on with the other drive in the meantime, open gparted as before - go to sdb1 - right clcik and run check

---

### Post by maphco on 2008-12-22
I don't have the option to "run check".  Only options it gies me are: delete, format to (then lists a bunch of different types I can format it to: ext2, ext3, etc.,), manage flags, and information.

Information just says: Warning
Unable to detect filesystem! Possible reasons are:
-the filesystem is damaged
-the filesystem is unknown to G Parted
-there is no filesystem available(unformatted)

---

### Post by wieman01 on 2008-12-22
Question... Do you have any important data on the laptop and would reinstalling a complete new system an option? If you don't need Xandros, I would just start from scratch.

---

### Post by Elfy on 2008-12-22
Try this from a terminal

```
sudo fsck /dev/sdb1
```

Post any output please, likely have to hope someone else is watching if you still have an issue.

I'll watch as I can see that wieman is still watching this :)

---

### Post by maphco on 2008-12-22
The laptop doesn't have any critical information.  The stuff that was on it can be found again on the net I suppose, shouldn't take me more than an hour or something like that to locate the stuff. Also, could you please tell me how to get rid of Xandras? That would be fabulous :P

---

### Post by maphco on 2008-12-22
forestpixie: your request returned:

fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?



And is this like a book for you?  Waiting in suspense for the next piece of the puzzle to be discovered? xD

---

### Post by maphco on 2008-12-22
The faces are "8 )" without the space.

---

### Post by Elfy on 2008-12-22
Yes it's like a book, some pages however are written in urdu, so I can't read them.

All I can say at the moment is that there's soemthing wrong woth the partition - wieman is likely to have more knowledge than me.

As far as removing xandros and reinstalling ubuntu then that's fairly simply accomplished. 

There's also some ntfs partitions do they have windows on?

---

### Post by maphco on 2008-12-22
Nope, no windows ever installed on this thing, least not by me. And urdu, is that from the Myth books? D'ni and stuff like that? :P ;)

And if I don't mind losing the information on sdb1 would formatting it get it back into a condition where I could reinstall the OS onto it?

---

### Post by Elfy on 2008-12-22
sorry no ntfs - a couple of small partitions which don't appear to have much and a restore partition.

Yes you can delete sdb1 and reinstall ubuntu to it - let ti write it's boot loader, at that point xandros would still be there, to remove that you would need to format the drive.

You could if you so wish start the ubuntu install - point it at sdb when you get to that part and tell it to use the whole disk.

Edit but if someone can say how to fix the disk error then you should be able to get it back.

---

### Post by maphco on 2008-12-22
Alright, well there isn't anythign on the laptop that is of major importance to me in any of the partitions. So what would you two suggest I do to start fresh on it? Do I format all the drives or what? Honestly, I don't know much of anything about partitions and stuff like that :(

If you could point me to some good resources on this stuff that would be terrific. As well, do you know any sites that give a good in depth look at the structure of the linux OS and how it works? I like to know everything xD But then again, what nerd doesn't? :D

---

### Post by maphco on 2008-12-22
I actually tried to reinstall Intrepid much earlier, but during the install it got stuck on "creating ext3 file system for / in partition #1 of SCSI2 (o,1,0) (sdb)..." and it wouldn't do anything :(

---

### Post by Elfy on 2008-12-22
> **maphco said:**
> I actually tried to reinstall Intrepid much earlier, but during the install it got stuck on "creating ext3 file system for / in partition #1 of SCSI2 (o,1,0) (sdb)..." and it wouldn't do anything :(

would make me wonder if there was a problem with the drive.

IF you don't have a problem losing partitions on that drive then delete sdb1 with the partition editor - apply and let it finish if you get an error come back with it.


If you're happy to start completely from scratch then I would mount root on sda, /home on sdb and swap on sdc myself

IF you wanted to do soemthing like that then you would want to remove all the partitions and just have 1 primary on each drive, but would need to swapoff and remove swap and extended as well on sdb

---

### Post by maphco on 2008-12-22
Alright forestpixie, I have no problem with experimentation at all.  How do you think I got into this predicament in the first place? :p

But seeing as this is totally new computer stuff that I've never worked with before I would like to have you take me through this step by step if that's okay with you.

---

### Post by Elfy on 2008-12-22
Before you do that can you try

```
smartctl -a
```

---

### Post by maphco on 2008-12-22
It says the program isn't installed.

---

### Post by wieman01 on 2008-12-22
Easiest way to reinstall is that you throw in the Ubuntu LiveCD and delete all partitions using the Partition Editor. That's a graphical tool and fairly straightforward. Just delete all partitions and create a single big one.

Once you have done that, install ubuntu on it.

---

### Post by maphco on 2008-12-22
wieman: Is there a proper way for me to delete them? Like a certain order or soemthing? I really don't want to screw it up beyond recoverability.

---

### Post by Elfy on 2008-12-22
You'll have to turn swapoff before you do anything to that - so right click on sdb5 and swapoff. Now delete sdb5 and apply, then you can select sdb1 and sdb2 in turn and delete and apply for them. Do the same for sdc1 and then sda1 -sda4.

At this point you have no formatted partitions on any of your disks. As you have 2 smallish drives I would create a swap partition on sdc, on both sda and sdb format the whole to ext3. You now have 3 partitions - start the install.

When you reach the partition part - choose manual - 

select what will likely be ref as sda1 - Edit - in the new window chhose use as ext3 and a mountpoint of / , close that window 

select sdb1 - Edit choose as ext3 - mountpoint needs to be /home, close 

Carry on with remainder of install.

---

