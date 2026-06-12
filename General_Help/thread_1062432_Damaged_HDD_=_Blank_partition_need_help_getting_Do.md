---
title: "Damaged HDD = Blank partition? need help getting Doc of bad HDD"
date: 2009-02-06
forum: General Help
---

### Post by rob1101 on 2009-02-06
Ok so a I have a laptop with a bad HDD and it will not boot (windows vista i believe). So anyway I booted up with the Ubuntu 8.04 live CD and it recognizes 3 partitions.
[LIST]
[*]TOSIBA SYSTEM VOLUME
[*]HDD RECOVERY
[*]and one with a bunch of random chars
[/LIST]

Ubuntu Reads HDD recovery and SYSTEM fine but it shows the 3rd (and largest) partition as being empty. I know this is simply not true. I have tried remounting it with the -t ntfs option, which was no good.

When I try to boot into the widows system I get a MBR error

My goal is just to get some user documents off the original windows system, doesn't really matter how that happens but I would like to have the pictures and music and such.

Thanks for any help.

---

### Post by caljohnsmith on 2009-02-06
I would recommend using "testdisk" to try and recover your documents from your Windows partition. On the Live CD, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
mv testdisk-6.10/linux/testdisk_static .

```
Then do:
```
sudo fdisk -lu
```
Find which is your main Windows partition as /dev/sdaX (like /dev/sda3 for example) and then do:
```
sudo testdisk_static /dev/[COLOR="Blue"]sdaX[/COLOR]
```
Choose "Proceed", "None", "Analyze", "Quick Search", and then you should see your Windows partition listed on the quick search screen. Press "p" to list its directory, and if that works OK, you can use the up/down and left/right arrow keys to navigate through your Windows directories, select each file you want to copy, and press "c" to copy whichever files you want to your Ubuntu desktop. Let me know how that goes or if you run into problems.

---

### Post by rob1101 on 2009-02-07
I did exactly what you said and then even did a "deep scan" and still could find no files :(

---

### Post by caljohnsmith on 2009-02-07
OK, how about following the previous directions again, but this time instead do:
```
sudo testdisk_static /dev/sda
```
And that way testdisk will look at your entire sda drive. Choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and if any of them appear to be your Vista partition. If you run into any problems, copy/paste everything in your terminal to the forums so I can get an idea of what happened. Also please be as specific as possible when describing any problems you run into.

---

### Post by rob1101 on 2009-02-07
It seems that the partition table may be messed up, before I scan I am prompted with this message

```

Disk /dev/sda - 80 GB / 74 GiB - CHS 9730 255 63

Warning: the current number of heads per cylinder is 255
but the correct value may be 128.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

```

im not sure how to, or if I should use this geometry tool. I will scan anyway and post back the results.

---

### Post by caljohnsmith on 2009-02-07
Definitely continue with the deep scan; if we need to, you can always run testdisk again with a different geometry setting (heads/cylinder) and try that, but try the default 255 heads/cylinder first. Also, how about posting:
```
sudo fdisk -lu
```
And identify the partition in question.

---

### Post by rob1101 on 2009-02-07
ok this is what the output looks like

```

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 80 GB / 74 GiB - CHS 9730 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  4051 254 63   65095317
D HPFS - NTFS              0  32 33   191  89 26    3072000 [TOSHIBA SYSTEM VOLUME]
D HPFS - NTFS            191  89 27  9091 130 63  142981120 [SQ004255V04]
* HPFS - NTFS           9091 131  1  9729  78 13   10246144 [HDDRECOVERY]









Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS found using backup sector!, 33 GB / 31 GiB

```The first item gives this error

```

   D HPFS - NTFS              0   1  1  4051 254 63   65095317



Can't open filesystem. Filesystem seems damaged.


```The others are fine excluding SQ004255V04 which still shows up as empty. 


```

root@ubuntu:/home/ubuntu/Desktop# fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x33d45e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   146055167    71490560    7  HPFS/NTFS
/dev/sda3       146055168   156301311     5123072   17  Hidden HPFS/NTFS

```ok I will try to use the geometry tool, and see what happens

---

### Post by caljohnsmith on 2009-02-07
How about also posting:
```
sudo mount /dev/sda2 /mnt && ls -l /mnt
df -h
```

---

### Post by rob1101 on 2009-02-07
not sure if i executed this correctly

```
 
root@ubuntu:/home/ubuntu/Desktop# mount /dev/sda2 /mnt && ls -l /mnt
total 0
root@ubuntu:/home/ubuntu/Desktop# df-h
-bash: df-h: command not found

```and i am confused about the geometry thing, I don't want  to mess this up more and make it any harder.

EDIT: DOH!

```

root@ubuntu:/home/ubuntu/Desktop# df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 220M   16M  204M   8% /lib/modules/2.6.24-16-generic/volatile
tmpfs                 220M   16M  204M   8% /lib/modules/2.6.24-16-generic/volatile
varrun                220M  104K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M   44K  220M   1% /dev
devshm                220M   12K  220M   1% /dev/shm
tmpfs                 220M   16K  220M   1% /tmp
/dev/sda2              69G   88M   69G   1% /media/SQ004255V04
/dev/sda2              69G   88M   69G   1% /mnt

```

---

### Post by caljohnsmith on 2009-02-07
Changing the heads/cylinder geometry within testdisk does not in itself change your HDD, but I believe that option is only relevant for the "quick search" results, not the "deep search" results. In other words, I believe you will get the exact same Deep Search results as you got before if you change the heads/cylinder geometry setting in testdisk. Unfortunately I think the bottom line is clear though: your sda2 partition is empty right now. Testdisk was not able to find any of its files, when you mounted the partition no files are there, and "df -h" shows that the sda2 partition is entirely free space. You could use some file recovery utility like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" (which is part of the testdisk suite of tools) to try and recover your files from sda2, but you will need another HDD at least as big as your sda2 partition to save all the recovered files to. You might want to check out this web page for other options:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Good luck and sorry for your loss.

---

