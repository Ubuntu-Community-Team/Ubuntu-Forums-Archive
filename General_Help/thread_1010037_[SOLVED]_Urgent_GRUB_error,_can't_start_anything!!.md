---
title: "[SOLVED] Urgent: GRUB error, can't start anything!!!"
date: 2008-12-13
forum: General Help
---

### Post by alsamman on 2008-12-13
guys, I was trying to install gfx grub yesterday but for some reason I was getting an error that it couldn't find /boot/grub/stage1 even though I went there and found it myself. I have installed gfx grub before and I haven't gotten this error before but yesterday I just decided to give up on it. Now I boot my computer today and grub doesnt start, its just a command prompt that looks like this:

grub>_

and I don't know what to do to fix this. I booted the liveCD and edited my menu.lst so that it looked like how it was before I tried to install gfx grub but it still won't work.

Please help fast, I need to study for an exam and I need to use ubuntu...

---

### Post by haylun98 on 2008-12-13
Go to Illustrated Dual Boot here: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Use Supergrub to reinstall your grub

Good luck studying alsamman

---

### Post by ajgreeny on 2008-12-13
Or just use your ubuntu live CD and follow the info below.

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by alsamman on 2008-12-13
> **haylun98 said:**
> Go to Illustrated Dual Boot here: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Use Supergrub to reinstall your grub

Good luck studying alsamman
thanks so much for the help but I am getting an error. When I downloaded supergrub onto usb and followed the instructions to put it on the USB, I booted and i get an error that says something like: NTLDR is missing press any key. Nothing happens when I do, it's not working:cry:

> **ajgreeny said:**
> Or just use your ubuntu live CD and follow the info below.

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

I tried this as well and when I boot my computer I get an error that says: Grub Loading Error 2 and nothing happens..

any ideassss?????????????????????

---

### Post by caljohnsmith on 2008-12-13
> **alsamman said:**
> thanks so much for the help but I am getting an error. When I downloaded supergrub onto usb and followed the instructions to put it on the USB, I booted and i get an error that says something like: NTLDR is missing press any key. Nothing happens when I do, it's not working:cry:



I tried this as well and when I boot my computer I get an error that says: Grub Loading Error 2 and nothing happens..

any ideassss?????????????????????
If you are using Intrepid, you are probably getting that Grub error 2 because you are using an older version of Grub that came with the gfxboot package; Intrepid now formats its ext3 partitions to use an inode size of 256 bytes instead of the 128 bytes that previous versions of Ubuntu use. The newer inode size causes older versions of Grub to choke. If you want to use gfxboot with Intrepid, make sure you have the latest gfxboot package from:

[http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

Since you can't boot into Ubuntu to fix it, how about booting your Live CD and please post the output of:
```
sudo fdisk -lu
```
And identify your /boot or Ubuntu partition that has Grub. Then I can help you install the newer gfxboot boot files to your Ubuntu partition from the Live CD if you would like a hand.

---

### Post by alsamman on 2008-12-13
> **caljohnsmith said:**
> If you are using Intrepid, you are probably getting that Grub error 2 because you are using an older version of Grub that came with the gfxboot package; Intrepid now formats its ext3 partitions to use an inode size of 256 bytes instead of the 128 bytes that previous versions of Ubuntu use. The newer inode size causes older versions of Grub to choke. If you want to use gfxboot with Intrepid, make sure you have the latest gfxboot package from:

[http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

Since you can't boot into Ubuntu to fix it, how about booting your Live CD and please post the output of:
```
sudo fdisk -lu
```
And identify your /boot or Ubuntu partition that has Grub. Then I can help you install the newer gfxboot boot files to your Ubuntu partition from the Live CD if you would like a hand.
Yeah I am using Intrepid, I forgot to change it in my sig but here is the output
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0b9e0b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   194868449    97434193+   7  HPFS/NTFS
/dev/sda2       194868450   390716864    97924207+   f  W95 Ext'd (LBA)
/dev/sda5       194868513   198965024     2048256   82  Linux swap / Solaris
/dev/sda6       198965088   390716864    95875888+  83  Linux
ubuntu@ubuntu:~$ 

```
I really don't care about gfx boot right now anymore lol, I just wanna get GRUB working again

---

### Post by caljohnsmith on 2008-12-13
OK, please boot the Intrepid Live CD (make sure its not a previous version), and try the following:
```
sudo mount /dev/sda6 /mnt
sudo cp /usr/lib/grub/i386-pc/* /mnt/boot/grub
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
If you are instead using 64-bit Intrepid, the above directory to copy from would be "/usr/lib/grub/x86_64-pc". Please post the output of all the above commands, reboot, and let me what happens.

---

### Post by alsamman on 2008-12-13
> **caljohnsmith said:**
> OK, please boot the Intrepid Live CD (make sure its not a previous version), and try the following:
```
sudo mount /dev/sda6 /mnt
sudo cp /usr/lib/grub/i386-pc/* /mnt/boot/grub
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
If you are instead using 64-bit Intrepid, the above directory to copy from would be "/usr/lib/grub/x86_64-pc". Please post the output of all the above commands, reboot, and let me what happens.

You are made of Win!

THANKS!

I ran all those commands, the first 2 didn't produce any output and then the next command took me to the grub command prompt and then root (hd0, 5) gave no output and then setup showed everything as successful!
I guess the first 2 commands were the ones I needed. Thank you so much and everyone else who helped out, I am really glad I got this working!

---

### Post by caljohnsmith on 2008-12-13
I'm glad to hear that did the trick; cheers and have fun with Ubuntu. :)

---

### Post by ajgreeny on 2008-12-14
For anyone else who has similar problems with grub, I found that copying the 8.10 grub listing from its own grub menu on a separate disk I use for testing distros, and pasting it into the grub menu for 8.04, my main distro, was not successful unless I changed the second line of the entry which used to say```
title        Ubuntu 8.10, kernel 2.6.27-9-generic
**root        (hd1,0)**
```but now says ```
title        Ubuntu 8.10, kernel 2.6.27-9-generic
**uuid        d71efa88-3f27-47df-a077-6d2ebb317999**
```back to the previous notation.  It had me baffled for quite a while until I noticed the difference in the way the entries were shown.  I assume this is because of the change in the inode size, but it was a big annoyance to me, until I tried the old way.

---

### Post by Robbyx on 2008-12-14
I am having the same grub error 2 on start up of my reinstalled system.

My root directory is sdb1 and the home sdb2. I set these up on the manual installation. I only reformatted sdb1.

What should I do?

Robin



```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    59842124    29921031   83  Linux
/dev/sdb2        59842125   122849054    31503465   83  Linux
/dev/sdb3       122849055   964815704   420983325    5  Extended
/dev/sdb4       964815705   976768064     5976180   82  Linux swap / Solaris
/dev/sdb5       122849118   205358894    41254888+  83  Linux
/dev/sdb6       205358958   410412554   102526798+  83  Linux
/dev/sdb7       410412618   964815704   277201543+  83  Linux
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo cp /usr/lib/grub/i386-pc/* /mnt/boot/grub
cp: target `/mnt/boot/grub' is not a directory

```

---

