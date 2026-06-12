---
title: "how to test SD read/write speed"
date: 2009-05-10
forum: General Help
---

### Post by macakinho on 2009-05-10
Hi!

Just got a brand new SD card off ebay, but bought it from a seller in Hong-Kong and when I got it, it wasn't the same brand as advertised... in fact, it didn't have any brand at all.. :(

It has a sticker in it saying it is a class 6 device.

How can I test its read/write speed?
Looked all over and found nothing for Linux...

Cheers!

---

### Post by StuartN on 2009-05-10
> **macakinho said:**
> How can I test its read/write speed?

Find out which device it mounts as and run hdparm -t. For instance, if I plug a USB pendrive in it mounts as /dev/sdb:

```
sudo hdparm -t /dev/sdb

/dev/sdb:
Timing buffered disk reads:   58 MB in  3.10 seconds =  18.70 MB/sec

```

---

### Post by macakinho on 2009-05-10
> **StuartN said:**
> Find out which device it mounts as and run hdparm -t. For instance, if I plug a USB pendrive in it mounts as /dev/sdb:

```
sudo hdparm -t /dev/sdb

/dev/sdb:
Timing buffered disk reads:   58 MB in  3.10 seconds =  18.70 MB/sec

```


Thank you! 
This only gave me the write speed though... Read the ma hdparm and didn't find any option to test the write or erase speed.
Any help here?

---

### Post by danwood76 on 2009-05-10
You can use DD to test disk speed, but it can easily lead to damaged data (partitions) if used incorrectly but is probably the most direct way of testing.

So for example my second internal disk is mount /media/HD2 so running this gives me the write speed:
```

dd count=1k bs=1M if=/dev/zero of=/media/HD2/test.img
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 7.69365 s, 140 MB/s

```
that command writes 1GB to the disk, this large number is because the filesystem on the device will speed up the transfer by caching the data if a small transfer is carried out.

--edit--
[COLOR="Red"]This is a VERY dangerous command if you miss-type the output file so obviously take care using it and be sure to type correctly![/COLOR]

---

### Post by macakinho on 2009-05-10
> **danwood76 said:**
> 
```

dd count=1k bs=1M if=/dev/zero of=/media/HD2/test.img
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 7.69365 s, 140 MB/s

```


Thanks! That did it!

I'm really disappointed now... 
sticker on SD card:    "Class 6"
terminal:              "1073741824 bytes (1.1 GB) copied, 212.248 s, 5.1 MB/s"
[wikipedia]("http://en.wikipedia.org/wiki/Secure_Digital_card") : "Class 4"


:-(:-(:-(

---

### Post by danwood76 on 2009-05-10
It could be your card reader/writer that is slower as opposed to the card?

---

### Post by macakinho on 2009-05-10
> **danwood76 said:**
> It could be your card reader/writer that is slower as opposed to the card?

humm.. how can I know that?
Will try a different SD card. One I know it's not class 6 and post tthe results here.

---

### Post by macakinho on 2009-05-10
On a SD card I though would be way slower:

"1073741824 bytes (1.1 GB) copied, 117.218 s, 9.2 MB/s"

damn it, those cheecky ebayers...  :(

---

### Post by elitenoobboy on 2009-08-23
> **danwood76 said:**
> 
```

dd count=1k bs=1M if=/dev/zero of=/media/HD2/test.img
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 7.69365 s, 140 MB/s

```
that command writes 1GB to the disk, this large number is because the filesystem on the device will speed up the transfer by caching the data if a small transfer is carried out.

If you use that command multiple times, is it normal for the speed to be lower on subsequent runs? The first time I ran it, creating a new file, test.img, I got 110MB/sec,* then each time after I run it, I get just under 50MB/sec. I changed to a different output file name, and the same thing happens, faster the first time at 114MB/s, then slower.

*the 110MB/sec is actually faster than what I get from the hdparm -t command: 90MB/s.

---

### Post by TiloBunt on 2011-08-31
> **danwood76 said:**
> You can use DD to test disk speed, but it can easily lead to damaged data (partitions) if used incorrectly but is probably the most direct way of testing.

So for example my second internal disk is mount /media/HD2 so running this gives me the write speed:
```

dd count=1k bs=1M if=/dev/zero of=/media/HD2/test.img
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 7.69365 s, 140 MB/s

```
that command writes 1GB to the disk, this large number is because the filesystem on the device will speed up the transfer by caching the data if a small transfer is carried out.

--edit--
[COLOR="Red"]This is a VERY dangerous command if you miss-type the output file so obviously take care using it and be sure to type correctly![/COLOR]


Thanks for this info, works like a charm,

I played around with the 1k(1000 times) and 1M (1 Mb file) to test my 16 GB SD card.
Keep in mind FAT32 formated card only support single files (thats why the second one gave me a file too large.
```

tilo@t-laptop:/media/5E33-82DF$ dd count=1k bs=1M if=/dev/zero of=/media/5E33-82DF/test0.img
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 113.36 s, 9.5 MB/s
tilo@t-laptop:/media/5E33-82DF$ dd count=2k bs=4M if=/dev/zero of=/media/5E33-82DF/test1.img
dd: writing `/media/5E33-82DF/test.img': File too large
1024+0 records in
1023+0 records out
4294967295 bytes (4.3 GB) copied, 285.687 s, 15.0 MB/s
tilo@t-laptop:/media/5E33-82DF$ dd count=1k bs=3M if=/dev/zero of=/media/5E33-82DF/test2.img
1024+0 records in
1024+0 records out
3221225472 bytes (3.2 GB) copied, 246.827 s, 13.1 MB/s
tilo@t-laptop:/media/5E33-82DF$ dd count=1k bs=3M if=/dev/zero of=/media/5E33-82DF/test3.img
1024+0 records in
1024+0 records out
3221225472 bytes (3.2 GB) copied, 269.524 s, 12.0 MB/s
tilo@t-laptop:/media/5E33-82DF$ dd count=1k bs=3M if=/dev/zero of=/media/5E33-82DF/test4.img
1024+0 records in
1024+0 records out
3221225472 bytes (3.2 GB) copied, 268.86 s, 12.0 MB/s
tilo@t-laptop:/media/5E33-82DF$ 


```

---

### Post by fuskeren on 2012-01-04
Hey guys
I tried this test, and now my ext. HD is... disfunctional. any hints on my f*** up?
please note.. I am a newbie at ubuntu

> **danwood76 said:**
> You can use DD to test disk speed, but it can easily lead to damaged data (partitions) if used incorrectly but is probably the most direct way of testing.

So for example my second internal disk is mount /media/HD2 so running this gives me the write speed:
```

dd count=1k bs=1M if=/dev/zero of=/media/HD2/test.img
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 7.69365 s, 140 MB/s

```
that command writes 1GB to the disk, this large number is because the filesystem on the device will speed up the transfer by caching the data if a small transfer is carried out.

--edit--
[COLOR="Red"]This is a VERY dangerous command if you miss-type the output file so obviously take care using it and be sure to type correctly![/COLOR]

---

### Post by danwood76 on 2012-01-04
You probably didn't read my instructions correctly and wrote zeros to the partition table of your disk. Probably over the first 1GB of data as well.

Depending on the original filesystem the data on the drive may be toast. A program like testdisk might be able to recover the data that was on there.

If there was no data on there just repartition using the Ubuntu disk utility.

---

### Post by tux-gamer on 2012-04-07
Hi, i find this thread from Google and i want to share something here.

You can test SD Card / MicroSD Card with **H2testtw 1.4**
I Use it with **wine 1.3.34** to test my MicroSD , i have **Visipro 16GB Class 10**

Info from **dmesg**
```

device eth1 entered promiscuous mode
usb 1-3: USB disconnect, address 21
usb 1-3: new high speed USB device using ehci_hcd and address 22
usb 1-3: New USB device found, idVendor=048d, idProduct=1336
usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 1-3: Product: Mass Storage Device
usb 1-3: Manufacturer: Generic
usb 1-3: SerialNumber: 00000000000006
scsi29 : usb-storage 1-3:1.0
scsi 29:0:0:0: Direct-Access     Generic  Storage Device   0.00 PQ: 0 ANSI: 2
sd 29:0:0:0: Attached scsi generic sg4 type 0
sd 29:0:0:0: [sde] 31291392 512-byte logical blocks: (16.0 GB/14.9 GiB)
sd 29:0:0:0: [sde] Write Protect is off
sd 29:0:0:0: [sde] Mode Sense: 03 00 00 00
sd 29:0:0:0: [sde] Assuming drive cache: write through
sd 29:0:0:0: [sde] Assuming drive cache: write through

```

and here the **h2testw** result:
[[IMG]http://img825.imageshack.us/img825/6758/h2testwv14microsdvisipr.th.jpg[/IMG]](http://img825.imageshack.us/i/h2testwv14microsdvisipr.jpg/)

I Hope it could help you guys.

---

### Post by sp88 on 2012-11-25
Hi,

The read write performance test can be done with the help of couple of tools available out there..Taking an average out of all of them will be a better way to determine the actual speed.
Some tools are as below:
fio
iozone
bonnie
dd
seeker
hdparm
etc...Some of the tools are explained here.
[read write performance test]("http://slashroot.in/linux-file-system-read-write-performance-test")

---

