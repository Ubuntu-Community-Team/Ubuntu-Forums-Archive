---
title: "Stubborn File"
date: 2009-04-17
forum: General Help
---

### Post by WatchingThePain on 2009-04-17
Hi Folks,

Can anyone help with this.

My external hd has ntfs which I access from Linux.

I have a problem file. It's an empty directory which when I try to delete I get "Input/Output error".

I have read/write permission (supposedly)
Tried rm -rf.
Also tried to delete via the inode.
Guess what..It doesn't have an inode.

Anyone good at blitzing this kind of file?.

---

### Post by iponeverything on 2009-04-17
> **WatchingThePain said:**
> Hi Folks,

Can anyone help with this.

My external hd has ntfs which I access from Linux.

I have a problem file. It's an empty directory which when I try to delete I get "Input/Output error".

I have read/write permission (supposedly)
Tried rm -rf.
Also tried to delete via the inode.
Guess what..It doesn't have an inode.

Anyone good at blitzing this kind of file?.

Check the extended attributes on the file.

take a look at this page:
[http://pagesperso-orange.fr/b.andre/extend-attr.html](http://pagesperso-orange.fr/b.andre/extend-attr.html)

---

### Post by xikarrousx on 2009-04-17
try opening terminal and typing:

gksu nautilus

then try deleting the file.. in most cases, this will let you take care of getting rid of that directory. 


post success :)

---

### Post by WatchingThePain on 2009-04-17
Thank you for the prompt replies.

Tried with Nautilus..no dice.
So if I edit extended settings maybe then I can delete it.
That might be the best course of action.

The drive is ntfs because I kept it when I dumped windows but these files were not put there by Windows.

I had to install net3g driver before the drive could be seen.
Just spotted another of these pesky files.

I dont think they can be moved either or I could move them to a partition then format the partition.

---

### Post by uncle-c on 2009-04-17
You definitely have read / write access to the ntfs drive ?


```
$ cat /etc/mtab
```

should confirm this.

---

### Post by egalvan on 2009-04-17
> **WatchingThePain said:**
> Hi Folks,

I have a **problem file**. **It's an empty directory **which when I try to delete I get "Input/Output error".

Anyone good at blitzing this kind of file?.

> **WatchingThePain said:**
> 
So if I edit extended settings maybe then I can **delete it.**

Just spotted another of these pesky files.
moved 
I dont think they can be **moved **either or I could move them to a partition then format the partition.

OK, I'm a bit confused...

1) are your talking about a FILE or a DIRECTORY... this should not make a difference, but I just want to cover bases...

2) do you want to **move** it (saving it) or do you want to **delete** it?


If you want to delete it ( and every thing you want/need has been saved or moved ) then just format that partition...it doesn't have to be empty to partition...

---

### Post by WatchingThePain on 2009-04-17
Lol I want to delete with extreme predjudice.
It's a folder.

---

### Post by egalvan on 2009-04-17
> **WatchingThePain said:**
> Lol I want to delete with extreme predjudice.


If you want to delete it

 ( and every thing you want/need has been saved or moved )

 then just format that partition...

it doesn't have to be empty to partition...


Using the PartedMagic LiveCD you can delete the partition completely.

(boot the CD, highlight the partition that you want to delete,
 then choose "delete",
 then "apply pending actions"
(details might differ depending on the version of PartedMagic))

---

### Post by ChaiTan on 2009-04-17
I had the same Input/Output error while trying to remove an empty directory on my External USB HD, partition type- ntfs. The only way I was able to fix it was through Windows.
Open a command prompt in windows and type:
chkdsk N: /F
where N: is the drive letter.

---

### Post by WatchingThePain on 2009-04-17
Windows is no longer an option for me.
I do not ever use it. The drive has ntfs but other than that I have no affiliation to Windows.

---

### Post by xikarrousx on 2009-04-17
safely unmount and remount?

what did uncle-c's suggestion output?

$ cat /etc/mtab

---

### Post by WatchingThePain on 2009-04-17
Anyway screw that stupid file. I will ignore it.
I reckon it might be a windoze virus that wishes it could work on ext3.
Can't help noticing that very touching picture Iponeverything.
A picture is worth a thousand words.

Here's my cat..no pun intended.

bash-3.2# cat /etc/mtab
/dev/sda3 / ext3 rw 0 0
none /dev ramfs rw 0 0
none /proc proc rw 0 0
none /sys sysfs rw 0 0
none /dev/pts devpts rw 0 0
none /dev/shm tmpfs rw 0 0
/dev/sda1 /boot ext2 rw 0 0
/dev/sda4 /home ext3 rw 0 0
/dev/sdb5 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
gvfs-fuse-daemon /home/main/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=main 0 0

Just looking at it I wonder what some of these are. I have Linux on the internal hd on various partitions. Then there's the usb external HD which is just all on the one partition.


I think sdb5 is the drive the things on.

---

### Post by ChaiTan on 2009-04-17
Then I dont think you can remove the directory, AFAIK there is no fsck for ntfs. I had Windows installed in VirtualBox and I fixed the partition through there.

---

### Post by WatchingThePain on 2009-04-18
Vitualbox is a good idea.
Thank you for that .
Cheers Everyone.

---

