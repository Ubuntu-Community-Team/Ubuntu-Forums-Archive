---
title: "First run on IBM ThinkPad T23 - GRUB Error 18"
date: 2008-12-03
forum: General Help
---

### Post by Aralhach on 2008-12-03
I installed Xubuntu normally on the laptop mentioned.  When the installation was over, it gave me that error, and quit.  The funny thing is that I just did the same install on another identical machine with no problems.

Any ideas?? :)

PS: On internet I read about disabling the IDE Translation in the BIOS, but we couldn't find that option in this BIOS.
PPS: I think I varied the hard drive size left for Windows from one install to the other.

---

### Post by caljohnsmith on 2008-12-03
A Grub error 18 typically occurs when you have a BIOS that cannot access anything on the HDD past either 8.5 GB or 137 GB, depending on how old the BIOS is. The easiest solution is to create a ~200 MB ext3 boot partition at the beginning of the drive, and then when you go through the installation, set the mount point on that partition as "/boot". That should hopefully be all it takes to fix your problem; good luck and let me know how it goes. :)

---

### Post by Aralhach on 2008-12-03
Thanks for the reply!! I noticed though that on the other install though, I left 18.3 GB on the Windows partition and it worked fine.  This other one (the one with the error) is 18236 MB,  That doesn't make sense to me.  I will try what you said though.

---

### Post by Aralhach on 2008-12-04
Thanks for the answers!
OK.... I put the boot at the beginning of the hard drive (although I went through quite a bit of hassle with the GParted thing) and it booted without the error, showing the GRUB.  The thing is that now the Windows partition doesn't boot.

One thing that happened during the partitioning is that an error occured while resizing the NTFS partition.  It kept mounting the disks while working, even when I told it explicitly to unmount them before the partitioning started.  After the bar got to the end a couple times, it started doing something else and then just mounted them for some stupid reason and the popped up with the error and quit.  However, the 200 MB were freed at the beginning of the drive, so I formatted it as an ext3 partition (it mounted the drives about 10 times, back and forth, when I told it to unmount one partition it mounted the other and so forth, until I finally got it to go without the error).

Now, it will boot into Xubuntu just fine, but it won't boot Windows at all (it says "Starting up...." and sits there idle).

I tried to put the WinXP CD in to repair the installation, and it just says "Press any key to boot from the CD..." and after pressing it, a message blinks quickly (I catch the words "Setup is inspecting" and I think "system") and then it goes blank and sits there (I think the hard drive light is on). But nothing....
I would really appreciate some help here!!!

---

### Post by caljohnsmith on 2008-12-04
Was Windows by chance the first partition on the drive, and then you moved its beginning point to make room for the 200 MB boot partition? If so, that's unfortunately a big problem; you didn't happen to mention in your original post that you had Windows installed too. How about first opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by Aralhach on 2008-12-04
Hmm, I thought I had.... Anyway, here's the output:
```
Disk /dev/sda: 30.0 GB, 30005821440 bytes
240 heads, 63 sectors/track, 3876 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x79337933

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    10689839     5344888+   7  HPFS/NTFS
/dev/sda2        10689840    58605119    23957640    f  W95 Ext'd (LBA)
/dev/sda5        10689903    40249439    14779768+   7  HPFS/NTFS
/dev/sda6        40249503    56246399     7998448+  83  Linux
/dev/sda7        56246463    58605119     1179328+  82  Linux swap / Solaris

Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4b0503f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             245     1999871      999813+   6  FAT16

```

Thanks for the reply!

---

### Post by caljohnsmith on 2008-12-04
Your sda drive shows an NTFS partition at the beginning of the drive, which I assume is Windows? It seems like that partition is a bit small for Windows though, so what is on the sda5 NTFS partition? I don't see a 200 MB linux partition at the beginning of the drive though; am I missing something? As far as linux goes, all I see is your Linux sda6 partition and the sda7 swap partition.

---

### Post by Aralhach on 2008-12-04
SORRY!! I posted the fdisk from the wrong computer. I'll repost it when I get the right one.

---

### Post by Aralhach on 2008-12-04
Sorry, here it is:
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      417690    37351124    18466717+   7  HPFS/NTFS
/dev/sda2        37351125    76180229    19414552+  83  Linux
/dev/sda3        76180230    78140159      979965    5  Extended
/dev/sda4              63      417689      208813+  83  Linux
/dev/sda5        76180293    78140159      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Aralhach on 2008-12-04
Should I open the partition editor from the LiveCD, format the NTFS partition, reinstall Windows, and then reinstall Xubuntu??

I can't boot the Windows CD either, it just locks up when I put it in.
I'd appreciate your replies!!!

---

### Post by caljohnsmith on 2008-12-04
It depends on how adventurous you are feeling. :) I know someone who was able to successfully fix their Windows XP after moving the beginning of its partition; it involves using testdisk to first fix the XP partition's boot sector, and then you have to manually edit some of the XP registry entries so that Windows can deal with being the second partition instead of the first one. But if you don't want to mess with it, I can understand, and in that case doing a full reinstall like you mentioned is probably your best option. It's up to you, but let me know if you are interested in fixing your Windows partition. Otherwise let me know how the reinstallation goes. :)

---

### Post by Aralhach on 2008-12-04
I'm interested in saving the files.  I did do backups of the hard drive, but I would rather have the files there.  Could you help me do the recovery??

Thanks a lot for your answers!!

---

### Post by caljohnsmith on 2008-12-04
Do you want to try and get Windows booting again, or do you just want to recover your important files from the partition? If it is the latter case, from the Live CD you could do:
```
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt
nautilus /mnt &
```
And hopefully that will be all it takes to access your Windows partition. If not, let me know, or let me know if you want to go through trying to fix Windows to the point of booting again. If you want to get Windows booting again though, I would have to PM my friend and you'll have to wait a bit until he can give you the details of how to do it.

EDIT: I forgot you're using Xubuntu; that second command above probably won't work then. Just pull up Xubuntu's file browser and browse to /mnt, and that's the same thing. :)

---

### Post by Aralhach on 2008-12-04
Thanks a lot for answering!!  I'm kind of in a hurry since this is not my computer, so I think I will just go for the clean re-install.  I would wait if it were mine (I still need to get a new HD for my other PC, I'm working on that).

Again, thanks a lot for your help!!!!

---

### Post by Aralhach on 2008-12-04
OK.... I opted for the clean install, as you know.  However, to get the Windows CD to boot I had to delete the boot partition.  Now, for Linux to run, should I leave the boot partition or absorb that space into the Windows partition....

Thanks again for all your help!!

---

### Post by caljohnsmith on 2008-12-04
> **Aralhach said:**
> OK.... I opted for the clean install, as you know.  However, to get the Windows CD to boot I had to delete the boot partition.  Now, for Linux to run, should I leave the boot partition or absorb that space into the Windows partition....

Thanks again for all your help!!
I'm not sure I understand exactly what you mean, but the bottom line is you'll want to get Ubuntu's boot files near the front of the drive to prevent the Grub error 18 you previously got. When you install Windows and use it to create a partition, can you make it leave some space (~200MB) at the beginning of the drive for your boot partition? From your post #9, the drive is only 40 GB, so most likely that computer's BIOS has the 8.5 GB limitation which caused the Grub error 18. If that's true, then you need to some how get Ubuntu's boot partition within the first 8.5 GB of the drive. If you create the boot partition first with Ubuntu, the Windows CD won't work? How about creating the 200 MB partition as FAT/NTFS and see if Windows doesn't mind that, and then you can reformat the 200 MB partition to ext3 once Windows installs.

---

### Post by Aralhach on 2008-12-05
You know what?? I was sick of it, so I said "Let's just do an install normally, with the boot partition".  Guess what.....  NO GRUB Error 18!!!!  This computer is just crazy.  The second time, it booted up Windows, but after the Windows screen started going, it gave me a Blue Screen, but Xubuntu, worked just fine.  I don't know.....  In the end, I just put Windows back on it, and left it there....... Sad end of story.

---

