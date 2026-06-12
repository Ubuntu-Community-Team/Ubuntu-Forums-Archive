---
title: "Recover disk content"
date: 2009-04-18
forum: General Help
---

### Post by orrie on 2009-04-18
I was going to install Windows XP on dual boot.
During the installation I noticed that my 3 disks was listed something like this:

```

137123 MB Disk 0 at Id 0 on bus 0 on atapi [MBR]
<the partiton that was sized to 1,5TB, /dev/sda/ This disk had ext3 fs.>

137123 MB Disk 0 at Id 0 on bus 0 on atapi [MBR]
<the windows partition that I was going to install to /dev/sdb/>

137123 MB Disk 0 at Id 0 on bus 0 on atapi [MBR]
<the ubuntu system disk with three partitions on /dev/sdc/ This disk have ext3 and swap>

```

All of these had the same Disk, Id and bus, and I found this very strange..
But I didn't think of it that much so I installed the WXP on the disk (/dev/sdb/).
After the installation, Windows XP was installed on that disk (/dev/sdb/) and the disk on the top (/dev/sda/) had now been changed to an partition with FAT16(wtf?) and 137GB on. (It was 1,3TB or something on it with ext3 fs.)
I've think I have lost all on that disk and have tried all night to fix this on some way.


***What have I done?***
I have just changed the type from FAT16 to Linux in cfdisk and written the partition table, but this didn't help of course..
Have also tried to recover this with an recovery tool in the Windows partition without any luck (just an annoying bluescreen of death!).
Right now I am trying to scan the disk with "gpart" to see if there is any results.


Right now it looks like this in cfdisk:
```

                          cfdisk (util-linux-ng 2.14)

                              Disk Drive: /dev/sda
                      Size: 1500301910016 bytes, 1500.3 GB
             Heads: 86   Sectors per Track: 15   Cylinders: 2271532

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        NC          Primary   Linux                           137438,96*
                            Pri/Log   Free Space                     1362862,51*

```



What should I do to perhaps get some of these files recovered again? (Hopefully they're not lost completely)
I hope anyone can help me on this one! :sad:

---

### Post by doas777 on 2009-04-18
well I would recomend that you download and burn off [UbuntuRescueRemix]("http://ubuntu-rescue-remix.org/") (but not to the affected areas of the disk), boot from it and try to recover the partition with [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"). if that fails, I would try [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to recover your userdata.
unfourtunatly the disk has most likely been formatted, and overwritten at that, so recovery may be problematic. 

good luck

---

### Post by amingv on 2009-04-18
DON'T do stuff on the HD you want to recover files from! It will just make recovery harder!!!

I've used [photorec]("http://www.cgsecurity.org/wiki/TestDisk_Download") to recover files from accidentally formatted hard drives with a pretty decent success rate. (Download the RPM for Linux and install it with alien; or the exe for Windows.)

When you choose where to put the recovered files **do not** pick the same HD/partition you're rescuing them from, pick another one.

I hope you good luck.

---

### Post by Hellstudios on 2009-04-18
Download parted magic and make a recovery CD, I use it all the time for stuff like this, (i experiment, don't judge me on how many times i accidentally format my HDD) it has all the programs you can think of to recover stuff.... it's basically an all in one rescue CD.


[http://partedmagic.com/](http://partedmagic.com/)


Instructions are pretty simple to burn it, just follow ones on instructables.com, I'm sure they have some.

---

### Post by orrie on 2009-04-18
How to use PhotoRec?



After the disk has been scanned with gpart, it looks like this:
```

root@ubuntu:~# gpart /dev/sda1 

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```
```

root@ubuntu:~# gpart /dev/sda  

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```

---

### Post by doas777 on 2009-04-18
start with testdisk first, as the partition was removed. you can find instructions in my link above. another one here: [http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

### Post by orrie on 2009-05-09
Allright doas, I'll try this thing out :-)
Haven't had any activity on the disk since this happening, so hopefully I can recover some of it :)


edit:
Allright!
For a month or so ago I was able to recover around 95% of the data I had on the disk.
At least the most most important (almost, just 2-5 files I didn't get).

Huge thanks to you doas!

---

