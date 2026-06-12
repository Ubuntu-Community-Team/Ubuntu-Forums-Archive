---
title: "Problems with grub, partition shows as wrong type?"
date: 2009-02-11
forum: General Help
---

### Post by Aroenai on 2009-02-11
I have a Toshiba Satellite P105-S9722 that came with a hidden Intervideo Express Media Player partition (251 MB). Pressing the media button to turn on the laptop loads the player, while the normal power button brings me to my dual boot Vista and Ubuntu 8.10 (using grub in the MBR). I want to be able to restart my computer and select the player instead of always having to shutdown first.

Doing a "fdisk -l" I get the following:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xddfaddfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34965   280854316    7  HPFS/NTFS
/dev/sda3           34966       38881    31455270    5  Extended
/dev/sda4           38882       38913      257040   88  Linux plaintext
/dev/sda5           34966       38714    30113811   83  Linux
/dev/sda6           38715       38881     1341396   82  Linux swap / Solaris

```

sda1 is Vista, sda5 and 6 are Ubuntu in the extended partition sda3. Sda4 is the last partition on the drive. For whatever reason the Ubuntu setup left a 1 MB area of unformatted space between sda1 and sda3 so that's why sda2 doesn't show up.

sda4 is the partition I'm trying to boot, and it shows as Linux plaintext (hex 88?). I dumped the partition to a file using "cat /dev/sda4 > ~/dump" and used "cat ~/dump | less" to search through the contents.

I found several references to sda and ext2, and the entry from its menu.lst (grub)

```
title Linux
kernel (hd0,3)/boot/bzImage root=/dev/sda4 vga=0x317
initrd (hd0,3)/boot/initrd-ivi
```

Adding this entry to the menu.lst in Ubuntu results in an error saying the partition can't be mounted. Is fixing this as easy as editing the partition table? How would I do that?

---

### Post by caljohnsmith on 2009-02-11
If you press your media button when you turn on the computer, can you still load the media player OK with your present setup? How about posting the output of the following:
```
sudo blkid -c /dev/null
sudo mount /dev/sda4 /mnt && ls -l /mnt
```

---

### Post by Aroenai on 2009-02-12
Yes, the media player still works.

xxxx:~$ sudo blkid -c /dev/null
[sudo] password for xxxx: 
/dev/sda1: UUID="909CA2D69CA2B5DE" LABEL="SQ004141P03" TYPE="ntfs" 
/dev/sda5: UUID="f18c4c34-e272-4f7b-978f-dd12c88a44e1" TYPE="ext3" 
/dev/sda6: UUID="629ec261-919e-4c1b-9c1d-61ff04176bb2" TYPE="swap" 
xxxx:~$ sudo mount /dev/sda4 /mnt && ls -l /mnt
mount: you must specify the filesystem type

---

### Post by caljohnsmith on 2009-02-12
How about trying the following entry in your Grub's menu.lst to boot your media player partition:
```
title Express Media Player
rootnoverify (hd0,3)
chainloader +1
```
And please let me know what happens when you try it from your Grub menu.

---

### Post by Aroenai on 2009-02-12
That was the first thing I tried before I dumped the partition looking for menu.lst, that didn't work either.

I'm guessing there's some code in the bios that looks for a partition with type 88 and changes it back to what it should be because it doesn't matter where the partition is on the drive, it will still load. If I change the partition type to 83 using cfdisk, the player no longer loads and it's identified as ext3 which isn't right. When I change it back to 88, everything works fine at least with the media button.

Further investigation in the dump of the partition shows that it's a 2.4 kernel and there were references to gcc with Ubuntu in the version number.


Maybe the dump of the partition and partition table would help? The dump compresses down to about 30.6 MB.

---

### Post by caljohnsmith on 2009-02-12
The "mount" command was not able to determine the file system type of your sda4 partition and mount it, nor was "blkid" able to figure out the file system. How about trying:
```
sudo vol_id --probe-all /dev/sda4

```
And please post the results.

---

### Post by Aroenai on 2009-02-12
```
xxxx:~$ sudo vol_id --probe-all /dev/sda4
[sudo] password for xxxx: 
xxxx:~$ 
```

What was that supposed to do?

---

### Post by caljohnsmith on 2009-02-12
So do you have any idea what file system sda4 is? Since linux can't mount that partition, Grub won't be able to mount it either, and thus you can't use the "kernel" "initrd" notation to boot it. I think about the only thing you can do is try to boot its boot sector with "chainloader", but we tried that and it doesn't work. If you can figure out how to mount the partition and access it, that would be a step in the right direction. Otherwise I don't think there's any way to use Grub to boot it.

---

### Post by Aroenai on 2009-02-12
I said earlier I think it's ext2 since that's what I kept seeing references to (along side references to sda4).

---

### Post by eeanm on 2009-03-02
Hey I'm having the same issue. Actually I would like to be able to mount the Express Media Player and see if its usable under normal Linux. But basically the same problem: I think it creates its own partitioning system. My guess is that we need to know some magic offsets to be able to mount it.

Have you figured anything else out?

---

