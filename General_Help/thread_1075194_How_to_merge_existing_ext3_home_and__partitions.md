---
title: "How to merge existing ext3 /home and / partitions"
date: 2009-02-20
forum: General Help
---

### Post by golfingmaniac89 on 2009-02-20
I have ubuntu installed with a separate /home partition. I am wanting to install Vista so that I can play games and use my printer, but my / and /home partitions are both primary and the Vista installer says that it cannot install because the maximum amount of primary partitions already exists. I want to merge the / and /home partitions into one primary partition so that I can install Vista. Is there any way of doing this without losing my data? Backing up everything I have and reinstalling ubuntu is not an option for me because I can't afford an external hard drive and I really don't want to go back through and reconfigure everything again. I have search all over the web and haven't found any solutions. Please, any help would be deeply appreciated.

---

### Post by dcstar on 2009-02-20
> **golfingmaniac89 said:**
> I have ubuntu installed with a separate /home partition. I am wanting to install Vista so that I can play games and use my printer, but my / and /home partitions are both primary and the Vista installer says that it cannot install because the maximum amount of primary partitions already exists. I want to merge the / and /home partitions into one primary partition so that I can install Vista. Is there any way of doing this without losing my data? Backing up everything I have and reinstalling ubuntu is not an option for me because I can't afford an external hard drive and I really don't want to go back through and reconfigure everything again. I have search all over the web and haven't found any solutions. Please, any help would be deeply appreciated.

Firstly, you have four Primary partitions so what else do you have installed?

If you really want to get rid of your /home partition (a bad idea, really) and have space in your root partition, then:

```
sudo mkdir /home2
cp -r /home /home2
```

Then reboot into recovery mode, comment out the /home entry in /etc/fstab and then do the other commands:

```
sudo gedit /etc/fstab
sudo mv /home /home.old
sudo mv /home2/ /home
```

Then reboot normally and use the partition editor to delete your old partition that held /home.

---

### Post by golfingmaniac89 on 2009-02-20
Here is my partition layout:

Partition-----Filesystem----Mountpoint----Size
--------------------------------------------------
/dev/sda1-----fat16-----------------------78.41M  
/dev/sda2-----ext3----------/-------------23.28G  <--- Primary
/dev/sda3-----ext3----------/home---------73.09G  <--- Primary
/dev/sda4-----extended---------------------1.95M  <--- Extended
- /dev/sda5---linux-swap-------------------1.95M  <--- Logical
unallocated---unallocated-----------------50.65G

The fat16 partition was already there (this is a Dell Inspiron 1720 Laptop). I want to merge /dev/sda2 with /dev/sda3 and install Vista in the unallocated space. Will the method above keep all of my settings since /home was originally on a separate partition?

---

### Post by Tony Flury on 2009-02-20
Why not create a bigger extended  partition - and put / and /home into seperate logical partitions in there - as far as I know / does not have to be a primary.

There are major benefits having / and /home seperate, which i assume you know already, and i would do anything you can to ensure to keep that.

---

### Post by caljohnsmith on 2009-02-20
Golfingmaniac89, it might be possible to simply change your partition table in order to convert your home partition into a logical partition. Then you wouldn't have to merge your home partition into your Ubuntu root partition, and you would have an extra primary partition to install Windows to. To see if that would be possible, how about posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by golfingmaniac89 on 2009-02-22
> **caljohnsmith said:**
> Golfingmaniac89, it might be possible to simply change your partition table in order to convert your home partition into a logical partition. Then you wouldn't have to merge your home partition into your Ubuntu root partition, and you would have an extra primary partition to install Windows to. To see if that would be possible, how about posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

Here is the output of "sudo fdisk -lu"

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      160649       80293+  de  Dell Utility
/dev/sda2          160650    48982184    24410767+  83  Linux
/dev/sda3        48982185   202258349    76638082+  83  Linux
/dev/sda4       202258350   206354924     2048287+   5  Extended
/dev/sda5       202258413   206354924     2048256   82  Linux swap / Solaris


and here is "sudo sfdisk -d"

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   160587, Id=de, bootable
/dev/sda2 : start=   160650, size= 48821535, Id=83
/dev/sda3 : start= 48982185, size=153276165, Id=83
/dev/sda4 : start=202258350, size=  4096575, Id= 5
/dev/sda5 : start=202258413, size=  4096512, Id=82

---

### Post by caljohnsmith on 2009-02-22
OK, we could shrink your sda2 linux partition just a little (only 63 sectors) so we could then make the sda3 linux partition a logical partition; then you will have an extra primary partition to install Windows to. Does that sound like a good plan? If so, how about doing the following from the Ubuntu Live CD:
```
sudo umount /dev/sda2; sudo e2fsck -f /dev/sda2
```
If the e2fsck completes without errors, proceed with:
```
sudo resize2fs /dev/sda2 48821472s
sudo e2fsck -fv /dev/sda2
```
Please post the output of all the above commands, and we can work from there.

---

### Post by golfingmaniac89 on 2009-02-26
> **caljohnsmith said:**
> OK, we could shrink your sda2 linux partition just a little (only 63 sectors) so we could then make the sda3 linux partition a logical partition; then you will have an extra primary partition to install Windows to. Does that sound like a good plan? If so, how about doing the following from the Ubuntu Live CD:
```
sudo umount /dev/sda2; sudo e2fsck -f /dev/sda2
```
If the e2fsck completes without errors, proceed with:
```
sudo resize2fs /dev/sda2 48821472s
sudo e2fsck -fv /dev/sda2
```
Please post the output of all the above commands, and we can work from there.

Thanks for the help, but I just decided to go ahead and reinstall everything. It was easier and wasn't as painful as I expected.

---

### Post by SaintDanBert on 2010-01-23
> **dcstar said:**
> 
Firstly, you have four Primary partitions so what else do you have installed? If you really want to get rid of your /home partition (a bad idea, really) and have space in your root partition, then:
```

sudo mkdir /home2
cp -r /home /home2

```
...


The command [highlight]cp -r [/highlight] will recursively walk the source folder tree, but it does not copy and preserve everything (links, special files, permissions, ownership, etc) that might be part of that folder tree.
Consider using:
```

sudo -i     # start a shell as the superuser [yea, I know its bad]
cd  /
cp --archive --recursive  /srcHome/  /dstHome/
logout      # or simply type CTRL-d (end of file)

```

The option [highlight]--recursive[/highlight] does everything that [highlight]-r[/highlight] does (and it does a better job of being documentation weeks later when you read the script).  The [highlight]--archive[/highlight] option is shorthand for [highlight]--recursive --no-dereferece --preserve=all[/highlight]. These options keep links intact as well as all permissions and ownership.
I know this does --recursive twice, but make it obvious for maintainability.

~~~ 0;-Dan

---

### Post by theozzlives on 2010-01-23
> **golfingmaniac89 said:**
> Thanks for the help, but I just decided to go ahead and reinstall everything. It was easier and wasn't as painful as I expected.

Probably a bad idea, but it's your computer and it's done.

---

