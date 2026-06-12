---
title: "Tried ! and Tried ! Ubuntu only setup one of my CDrom Drivs"
date: 2006-07-12
forum: Desktop Environments
---

### Post by orb9220 on 2006-07-12
Ok I know they did work before I did a reinstall to get all my partions organized.

1) Disks program see's it as hdb
2) Put disk in any disk and flashes and flashes then led stays on no icon on desk no listing in nautilas.

fstab only shows one cdrom:

/dev/hdc        /media/cdrom    udf,iso9660   user,noauto     0       0

I tried to add:

/dev/hdb        /media/cdrom0    udf,iso9660   user,noauto     0       0
I have tired                1 there
i have left off the 0 and 1
I have created folders file system there is a cdrom with red slash circle
and cdrom0 also cdrom1
There are cdrom cdrom0 folders in /media
Why originally is thier a cdrom folder in filesystem and /media makes it confusing.

What I need is to have both show up on desktop double click and walla chango I can look what are on the disks.

And to copy files off of cd's,dvd's and udf disk.
I need them adjusted so that anybody or program can read,burn,push the button to eject. Just like on XP!

Any Help on this would be appreciated and I am searching the fourums and continuing to try myself.

](*,) Oh My! ](*,)

---

### Post by taavi on 2006-07-12
> **orb9220 said:**
> Ok I know they did work before I did a reinstall to get all my partions organized.

1) Disks program see's it as hdb
2) Put disk in any disk and flashes and flashes then led stays on no icon on desk no listing in nautilas.

fstab only shows one cdrom:

/dev/hdc        /media/cdrom    udf,iso9660   user,noauto     0       0

I tried to add:

/dev/hdb        /media/cdrom0    udf,iso9660   user,noauto     0       0
I have tired                1 there
i have left off the 0 and 1

Those 0 and 1 there are nothing to do with your cd-rom drive being recocnized by Ubuntu or any Linux system. From man fstab you can read: "[I]The fifth field, (fs_freq), is used for these filesystems by the dump(8) command to determine  which  filesystems need to be dumped.  If the fifth field is not present, a value of zero is returned and dump will assume that the filesystem does not need to be dumped. 

The sixth field, (fs_passno), is used by the fsck(8) program to  determine  the  order  in which  filesystem checks are done at reboot time.  The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno  of  2. Filesystems within  a  drive will be checked sequentially, but filesystems on different drives will be        checked at the same time to utilize parallelism available in the hardware.  If  the  sixth field  is  not  present or zero, a value of zero is returned and fsck will assume that the filesystem does not need to be checked.[/I]"

Before you add any lines to your fstab you have to be sure about your computers setup, right? Those names 'hdb' and 'hdc' and so on are representing IDE disks ... -- 'hda' is IDE 0 cables's master and 'hdb' is slave drive, thus 'hdc' IDE 1 master and 'hdd' IDE 1 slave drive. So you have to be sure what cable is connected to which drive and is this master or slave you are using. You can do some research without digging into your PC like that:

```
dmesg | grep "hdc:"
```what gives in my PC right now:```
$ dmesg | grep hdc:
[17179576.836000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[17179578.532000] hdc: _NEC CD-RW NR-9100A, ATAPI CD/DVD-ROM drive
[17179579.412000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)

``` And I read out that IDE 1 master drive is NEC CD-RW... You can of course scan all your drives changing grep parameter "hda:", "hdb:" etc...

---

### Post by orb9220 on 2006-07-12
Good info !

Thanks for the help.

But when I booted to the XP Dark Side and tried to read disk I got a popup that read.

   "Oh! My God Ubuntu killed Kenny" 
 "You traitor come back to the Dark Side"

I guess the drive which was an older MSI dr4-a could not live in the Ubuntu
World Oh well.

---

