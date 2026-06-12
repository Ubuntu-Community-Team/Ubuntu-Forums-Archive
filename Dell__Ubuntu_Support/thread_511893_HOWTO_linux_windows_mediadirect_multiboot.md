---
title: "HOWTO: linux windows mediadirect multiboot"
date: 2007-07-28
forum: Dell  Ubuntu Support
---

### Post by HadroLepton on 2007-07-28
i have managed to get linux, windows, and mediadirect to work in multiboot

some background information: i have a dell inspiron 640m (e1405). delivered with the notebook was windows vista and mediadirect 3.

what you get
[LIST]
[*]windows, linux, and mediadirect
[*]grub installed in mbr of harddisk
[*]grub can boot linux, windows, and if you like, mediadirect
[*]the mediadirect button will boot mediadirect
[/LIST]

what you need
[LIST]
[*]windows installation cd
[*]mediadirect installation cd
[*]linux installation cd
[*]system rescue cd ([http://www.sysresccd.org](http://www.sysresccd.org)) or other capable live cd
[*]external harddisk or other external mass storage
[*]backup of all your data.
[/LIST]

NOTE! you must backup your data. all data on your harddisk will be lost when mediadirect repartitions your harddisk.

also note: i do not have the notebook in front of me while writing this. it can happen that i make some mistakes. don't just copy the commands, pay attention to what you do before you do it. please read and understand all the steps before you start. this guide is not newbie friendly, if you don't know what a partition is or what a mbr is then ask a knowledgeable friend to assist you.

overview of the steps
[LIST=1]
[*]let mediadirect cd create partition layout
[*]install windows on prepared partition
[*]install mediadirect from windows
[*]save a directory from the windows partition created by mediadirect
[*](optional) save an image of the mediadirect partition
[*]setup partition for multiboot
[*]install windows, copy the directory saved previously
[*]install linux
[*]enjoy
[/LIST]

steps in detail

**let mediadirect cd create partition layout**
WARNING! this is the part where you lose all data on you harddisk
[LIST]
[*]boot from the mediadirect cd
[*]follow the steps and let the cd create the partition layout for you
[/LIST]
the cd will create following layout:

sda1: a small disguised fat16 partition with some files on it. i don't know what they are for
sda2: unformatted ntfs partition
sda4: extended partition
sda5: a disguised fat32 partition. but it is not empty, the cd writes some hidden information and will refuse to install if it is not there later

**install windows on prepared partition**
[LIST]
[*]boot from the windows cd and install to the second partition
[/LIST]
nothing special here, just follow the steps

**install mediadirect from windows**
[LIST]
[*]boot into windows
[*]insert mediadirect cd and start the installation
[/LIST]
also nothing special here, just follow the steps

NOTE! do not boot into mediadirect yet. if you boot mediadirect it will setup some stuff and i don't know what implications it will have if we change the partition layout and reinstall windows later. also if you want to save an image of the mediadirect partition you will want to keep it unused. see also the save image step.

**save a directory from the windows partition created by mediadirect**
the mediadirect installation process created the directory c:/MDT in the root of the windows partition
[LIST]
[*]copy the directory c:/MDT to your external storage
[/LIST]
note: there are some other directories created but they seem to be not necessary for mediadirect to work
also note: my external storage was an usb harddisk formatted using ext3. since windows cannot read/write to ext3 i used system rescue cd to copy the directory. see also next step.

**(optional) save an image of the mediadirect partition**
this is optional but highly recommended. when something goes bad later and you need to reinstall mediadirect you can restore from the image. otherwise you need to repeat all these steps.
there are many ways to save an image of a partition. you can use your favorite tool if you like. just remember to save the image to an external storage because the harddisk will have to be repartitioned again.
here is how i saved the image
[LIST]
[*]boot using system rescue cd
[*]mount your external storage
```

cd /mnt
mkdir sdb1
mount /dev/sdb1 sdb1
cd sdb1

```
[*]create the image using dd
be very carefull when working with dd, one typo can kill all your data. make sure you know what you do before pressing enter
```

dd if=/dev/sda5 | gzip > mediadirectimage.dd.gz

```
you can restore the image using
```

gzip -dc mediadirectimage.dd.gz | dd of=/dev/sda5

```
note when you have a fat32 partition as external storage there is a filesize limit of 4gb. the mediadirect partition is only 2gb so there should be no probem.
[*]i recommend you also save the partition layout, just in case
```

sfdisk -d /dev/sda > partitionlayout.txt

```
you can later restore the partition layout using
```

sfdisk < partitionlayout.txt

```
keep in mind that you can lose all data on harddisk if you do this
[/LIST]

**setup partition for multiboot**
now we repartition the harddisk to make space for linux. there are some limitations on how you can place your partitions.

sda2 must be the windows partition, and i think it must be ntfs (size does not matter)
sda4 must be extended partition
sda5 must be the mediadirect partition

you can use your favorite partitioning tool. i used ranish partition manager from the system rescue cd (type ranish at the boot prompt of the cd).
i created following layout

sda1: 10gb ext3 for linux
sda2: 15gb ntfs for windows
sda3: 50gb fat32 for data
sda4: 2gb extended
sda5: 2gb disguised fat32 for mediadirect

note that i did not touch sda4 and sda5. it was left as created by the mediadirect cd

**install windows, copy the directory saved previously**
[LIST]
[*]boot using windows cd and install to the second partition
[*]restore the directory c:/MDT saved previously
[/LIST]

**install linux**
[LIST]
[*]boot using ubuntu cd and install linux to the first partition
[/LIST]

note: the installation process will recognize the windows and mediadirect partition and will make entries for them in grub and in fstab.

if you want to boot mediadirect from grub: edit the grub configuration file (/boot/grub/menu.lst). scroll all the way down. here should be one entry for windows and one entry for mediadirect, remove the line "makeactive" from the mediadirect entry.

**enjoy**
yaay :)

please comment for bugs or typos

also please vote for free software mediadirect
[http://www.dellideastorm.com/article/show/72033/use_free_software_for_mediadirect](http://www.dellideastorm.com/article/show/72033/use_free_software_for_mediadirect)

---

### Post by Farthen on 2008-01-16
worked fantastic, thanks

(also tried many other "Howtos" all didn't work)

Have an Inspiron 1520 with 160GB hdd and mediadirect 3.3


Now I have MediaDirect, Ubuntu and Windows, so I can watch more movies without A/C :popcorn:

---

