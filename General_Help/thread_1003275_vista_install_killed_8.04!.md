---
title: "vista install killed 8.04?!?"
date: 2008-12-05
forum: General Help
---

### Post by dlm4849 on 2008-12-05
I guess I can't leave well enough alone...I decided I wanted to install Vista on my laptop to do some light gaming with. Got my 8.04 boot cd and resized a large NTFS partition that I keep my music on, which went well. The resized partition still works fine, but after I installed Vista, as expected, the grub menu didnt come up.

Per usual, I loaded up my live cd of 8.04 to repair grub on my ubuntu install and to my horror, instead of seeing two ext3 partitions (one for /home and other for the rest) I see nothing but my ntfs patition that has my music on it, the vista partition, swap and about 13 gigs of unallocated space. I couldnt find my home partition in the file manager and it seems my ubuntu install has vanished. I would really like to save it, as there are some important documents that were not backed up. Ironically enough, the stuff I backed up was the stuff on the ntfs partition, since it was the one being resized.

---

### Post by utsuprainfra on 2008-12-05
> **dlm4849 said:**
> I guess I can't leave well enough alone...I decided I wanted to install Vista on my laptop to do some light gaming with. Got my 8.04 boot cd and resized a large NTFS partition that I keep my music on, which went well. The resized partition still works fine, but after I installed Vista, as expected, the grub menu didnt come up.

Per usual, I loaded up my live cd of 8.04 to repair grub on my ubuntu install and to my horror, instead of seeing two ext3 partitions (one for /home and other for the rest) I see nothing but my ntfs patition that has my music on it, the vista partition, swap and about 13 gigs of unallocated space. I couldnt find my home partition in the file manager and it seems my ubuntu install has vanished. I would really like to save it, as there are some important documents that were not backed up. Ironically enough, the stuff I backed up was the stuff on the ntfs partition, since it was the one being resized.


strange.  you had 

/dev/nftsMUSIC
/dev/home
/dev/root
/dev/swap

and shrunk /dev/ntfsMUSIC

so you should have the others...

do you remember what the device names were for /dev/home and /dev/root?

---

### Post by adamant715 on 2008-12-05
Try Installing vista first, then install Ubuntu. Because you installed Vista first it overwrited the GRUB bootloader     therefore only booting into Vista.

So since Vista is Installed, when you install Ubuntu on a separate partition it will use the GRUB Bootloader instead of windows' default one.

---

### Post by dlm4849 on 2008-12-05
> **utsuprainfra said:**
> strange.  you had 

/dev/nftsMUSIC
/dev/home
/dev/root
/dev/swap

and shrunk /dev/ntfsMUSIC

so you should have the others...

do you remember what the device names were for /dev/home and /dev/root?

That's why Im so confused. I didnt touch the other two partitions, but theyre the ones that messed up. I dont remember what the device names were. I didnt change them so would they still be whatever the default is?

> **adamant715 said:**
> Try Installing vista first, then install Ubuntu. Because you installed Vista first it overwrited the GRUB bootloader therefore only booting into Vista.

Id rather try to fix this one. Ive run into this problem before and I think its fixable, but its just a special case (hopefully). If I end up having to, I will be doing what you suggest.

---

### Post by utsuprainfra on 2008-12-05
> **dlm4849 said:**
> That's why Im so confused. I didnt touch the other two partitions, but theyre the ones that messed up. I dont remember what the device names were. I didnt change them so would they still be whatever the default is?



Id rather try to fix this one. Ive run into this problem before and I think its fixable, but its just a special case (hopefully). If I end up having to, I will be doing what you suggest.

I'm sort of afraid that Vista installed on to your old root and home partitions.  Do you remember how much room you made for Vista?

---

### Post by dlm4849 on 2008-12-05
yes, about 25 gigs. Its on the correct partition. I had about 13 gigs b/w /home and /root, so that checks out.

---

### Post by zvacet on 2008-12-06
>  I see nothing but my ntfs patition that has my music on it, the vista partition, swap and about **13 gigs of unallocated space**.

> I had about 13 gigs b/w /home and /root, so that checks out.

If this is correct it look that you deleted Ubuntu partition,because now you have 13GB of unallocated space.Try with Ubuntu live CD

```
sudo fdisk -l
```

and post output.

---

### Post by dlm4849 on 2008-12-06
sorry double post.

---

### Post by dlm4849 on 2008-12-06
I did that and got the same output as mentioned in my first post. Theres no way I could have deleted the partition. All I did was resize the NTFS and the install Vista.

I made the connection with the 13 gigs of unallocated space and whatnot, but it just doesnt make any sense.

---

### Post by dlm4849 on 2008-12-06
Sorry, must have still been half asleep or something when I made that last post. I booted back into my livecd and heres a screen of gparted.

And here's the output of fdisk:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1938    14651248+   5  Extended
/dev/sda2            1939       17558   118085782+   7  HPFS/NTFS
/dev/sda3   *       17558       20674    23550976    7  HPFS/NTFS
/dev/sda5            1680        1938     1951866   82  Linux swap / Solaris

```

Seems like the boot should be marked on sda1, right? Whats weird is that the ext filesystem will not show under ubuntu on the live cd. I can't access it through grub to try and reinstall grub back to sda1 either.

---

### Post by TeXtonyx on 2008-12-06
Download the Super Grub Disk, it will come in handy in other
situations too. Use it with the help (gives advice) enabled. If you
have a bootable ext3 type 83 it will find it.

I think you should double-check your gparted results. Boot up
with the live install cd, and run sudo fdisk -l and make sure
that your ext 3 partition is missing. If it is, maybe you can
recover the partition... I've seen Testdisk have some success.

EDIT: I just looked at your screenshot. Doesn't it say you have
12.1GB unallocated space where you would expect your ext3 to be?

---

### Post by dlm4849 on 2008-12-06
That last post was from my live cd. I will check out super grub disk.

---

### Post by dlm4849 on 2008-12-06
Anyone else have any insight?

---

### Post by zvacet on 2008-12-06
@ **dlm4849**

I looked screen shot of your partition table and yes you have extended partition,but inside of it you have unallocated space and swap.On that unallocated space you once had Ubuntu,but not anymore.Sorry for bad news.If I´m wrong let somebody correct me.I´ll be glad if I´m wrong.

---

### Post by dlm4849 on 2008-12-06
> **zvacet said:**
> @ **dlm4849**

I looked screen shot of your partition table and yes you have extended partition,but inside of it you have unallocated space and swap.On that unallocated space you once had Ubuntu,but not anymore.Sorry for bad news.If I´m wrong let somebody correct me.I´ll be glad if I´m wrong.

Thats what Im figuring, but I just can't for the life of me figure out how this would have happened. Im going to wait for a while and keep bumping this to see if anyone thinks of anything.

Thanks

---

### Post by utsuprainfra on 2008-12-06
> **dlm4849 said:**
> Sorry, must have still been half asleep or something when I made that last post. I booted back into my livecd and heres a screen of gparted.

And here's the output of fdisk:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1938    14651248+   5  Extended
/dev/sda2            1939       17558   118085782+   7  HPFS/NTFS
/dev/sda3   *       17558       20674    23550976    7  HPFS/NTFS
/dev/sda5            1680        1938     1951866   82  Linux swap / Solaris

```

Seems like the boot should be marked on sda1, right? Whats weird is that the ext filesystem will not show under ubuntu on the live cd. I can't access it through grub to try and reinstall grub back to sda1 either.

Can you boot live and then mount /dev/sda1 to /mnt/wherever to mmake sure your data is there?  At least it's still an ext fs, that looks good.

---

### Post by dlm4849 on 2008-12-06
can you elaborate a little? its asking to specify filesystem type and Im not sure how to do that.

---

### Post by zvacet on 2008-12-07
This is little workaround.Install [fs driver]("http://www.fs-driver.org/") on your Vista partition.During installation it will ask whitch partition you want to see and you will point to the partition with your possible Ubuntu system on.If you have any Ubuntu files you should be able to see them from Vista.

---

### Post by dlm4849 on 2008-12-07
I guess all my stuff really is gone...windows asks to format the partition when I try to access through fs driver.

---

### Post by zvacet on 2008-12-07
Sorry,but it look like you will need to install Ubuntu again.

---

### Post by utsuprainfra on 2008-12-07
> **dlm4849 said:**
> can you elaborate a little? its asking to specify filesystem type and Im not sure how to do that.

well, what FS were they?  

sudo mount -t ext3 /dev/sdXY /mnt/point

---

### Post by dlm4849 on 2008-12-07
hmm...says:
```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/disk-2
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[  205.492399] wlan0: RX AssocResp from 00:1c:10:a6:08:58 (capab=0x401 status=0 aid=3)
[  205.492407] wlan0: associated
[  205.499523] wlan0: authentication frame received from 00:1c:10:a6:08:58, but not in authenticate state - ignored
[  205.500687] wlan0: association frame received from 00:1c:10:a6:08:58, but not in associate state - ignored
[  205.504123] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  221.579220] wlan0: no IPv6 routers present
[  266.007020] attempt to access beyond end of device
[  266.007031] sda1: rw=0, want=4, limit=2
[  266.007038] EXT3-fs: unable to read superblock
[  271.358192] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO

```

Does that mean there isnt anything there?

---

### Post by utsuprainfra on 2008-12-08
> **dlm4849 said:**
> hmm...says:
```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/disk-2
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[  205.492399] wlan0: RX AssocResp from 00:1c:10:a6:08:58 (capab=0x401 status=0 aid=3)
[  205.492407] wlan0: associated
[  205.499523] wlan0: authentication frame received from 00:1c:10:a6:08:58, but not in authenticate state - ignored
[  205.500687] wlan0: association frame received from 00:1c:10:a6:08:58, but not in associate state - ignored
[  205.504123] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  221.579220] wlan0: no IPv6 routers present
[  266.007020] attempt to access beyond end of device
[  266.007031] sda1: rw=0, want=4, limit=2
[  266.007038] EXT3-fs: unable to read superblock
[  271.358192] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO

```

Does that mean there isnt anything there?

Ok, my advice is to do a total hard disc image backup (if possible, think network and leave over a weekend or something) along with new partitions that matter backups.  Then proceed with the following:

[http://kubuntuforums.net/forums/index.php?topic=3098527.0](http://kubuntuforums.net/forums/index.php?topic=3098527.0)

---

### Post by dlm4849 on 2008-12-08
Ive never done anything like this before, so I want to be sure in what I do before I do it.

From what I get from that thread is that I should use testdisk to find out what the specs of my hard disk were before it messed up and then try to create partitions with those exact specs?

I dont much care if I lose vista, I only installed it for poops and giggles and maybe to play a couple games on it, but I think if I put windows on this computer again, it'll be xp pro.

---

### Post by muuu on 2009-01-17
Hi, i had the same problem. Luckily i found my partition by using TestDisk's deep search. So i backed up my impotent files, and deleted the partition.

And then i did some testing. I found that the Windows Vista/7 installer, removed any partition Ubuntu was installed on.
When i started Gparted from a usb stick, the ext2 partition was gone along with a NTFS partition.
I tried the other filesystems, but the result was the same. If ubuntu was installed on a partition, the partition would be deleted.

This is how it looked before i started the Windows Vista/7 installer:
/dev/sda1 primary fat32 PQSERVICE (Acer system restore partition)
/dev/sda2 primary NTFS ACER (Vista partition)
/dev/sda3 primary NTFS DATA (Empty partition for users files)
/dev/sda4 extended 
/dev/sda5 logical NTFS (Empty partition W7 for installation)
/dev/sda6 logical ext2 (My Ubuntu installation)
/dev/sda7 linux-swap

And after:
/dev/sda1 primary fat32 PQSERVICE (Acer system restore partition)
/dev/sda2 primary NTFS ACER (Vista partition)
/dev/sda3 primary NTFS DATA (Empty partition for users files)
/dev/sda4 extended 
unallocated
/dev/sda5 linux-swap

And all i did, was starting the Vista/7 installer, and then quit and reboot.

---

