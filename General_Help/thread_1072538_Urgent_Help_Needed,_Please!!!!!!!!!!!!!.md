---
title: "Urgent Help Needed, Please!!!!!!!!!!!!!"
date: 2009-02-17
forum: General Help
---

### Post by ksanthosh77 on 2009-02-17
Hi All,

        I have 160 Gb Hard disk filled with,


120 GB Windows partion splitted as C:,D:,E:,F:

remaining 35 GB, i used for Ubuntu and mandriva.

Today, i got Redhat EL 5 server cd's and i planned to install, so i booted and get into the steps. after the few installation  step, suddenly it asks for partitioning and i proceeded with Erase ALL data. within one second i saw the custom layout(partitioning) as 160 Free. and i suddenly rebooted the system to avoid proceeding, my grub was gone, i cant find out all the partition, now i m using ubuntu live cd to tying this message and connecting internet. 

If i give the following command in Ubuntu live cd it shows:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 

i m very sad, please help to recover my partions. I think,it wont loss because i wont start the installation.

Idont know 
Idont know wat to do,

Urgent very...:(

---

### Post by oldos2er on 2009-02-17
You could try installing testdisk while running your LiveCD.

---

### Post by caljohnsmith on 2009-02-17
I agree with oldos2er, I think your best bet is to give testdisk a try to see if it can recover your partitions. How about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and which ones seem to be the ones you want to recover. We can work from there if you want.
===========================

---

### Post by ksanthosh77 on 2009-02-18
Hi caljohnsmith,

Thanks for your information and I tried wat you dicussed above. I have confusion in selecting the partition

see here,
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  2548 254 63   40949622 [Windows]
D HPFS - NTFS           2549   0  1  3823 254 63   20482875 [songs]
D HPFS - NTFS           3824   1  1  6373 254 63   40965687 [studies]
D HPFS - NTFS           6374   1  1  8923 254 63   40965687 [softwares]
D HPFS - NTFS           8924   1  1 10198 254 63   20482812 [funs]
D HPFS - NTFS          10199   1  1 11464 254 63   20338227 [Extra]
D HPFS - NTFS          11465   1  1 12647 254 63   19004832 [General]
D Linux                12648   1  1 15701 254 63   49062447
D Linux                15702   1  1 15713 254 63     192717
D Linux Swap           15714   1  1 16078 254 63    5863662
D Linux                16079   1  1 16929 254 63   13671252
D Linux                16930   0  1 17056 254 63    2040255
D Linux                17057   1  1 18340 254 63   20627397
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,


when i Press  P it shows segmenation fault and exit to the terminal.

**Now my question is i want all the partition above stated. how to proceed further???**


I m online now.

---

### Post by ksanthosh77 on 2009-02-18
Hi cal,

Please follow up to the above thread.

      I tried with recover test disk and it asks for write to partition table i wrote it. but the thing is when i rebooted the machine it will results in Grub 17 error, i cant get the boot loader. can i reinstall grub or how to do?

---

### Post by caljohnsmith on 2009-02-18
Ksanthosh77, please be patient and observe the forum rules of not bumping your thread more often than every 24 hours. I will answer your thread when I get a chance.

---

### Post by hyper_ch on 2009-02-18
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by caljohnsmith on 2009-02-18
> **ksanthosh77 said:**
> ```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] HPFS - NTFS              0   1  1  2548 254 63   40949622 [Windows]
[COLOR="Red"]L[/COLOR] HPFS - NTFS           2549   0  1  3823 254 63   20482875 [songs]
[COLOR="Red"]L[/COLOR] HPFS - NTFS           3824   1  1  6373 254 63   40965687 [studies]
[COLOR="Red"]L[/COLOR] HPFS - NTFS           6374   1  1  8923 254 63   40965687 [softwares]
[COLOR="Red"]L[/COLOR] HPFS - NTFS           8924   1  1 10198 254 63   20482812 [funs]
[COLOR="Red"]L[/COLOR] HPFS - NTFS          10199   1  1 11464 254 63   20338227 [Extra]
[COLOR="Red"]L[/COLOR] HPFS - NTFS          11465   1  1 12647 254 63   19004832 [General]
[COLOR="Red"]L[/COLOR] Linux                12648   1  1 15701 254 63   49062447
[COLOR="Red"]L[/COLOR] Linux                15702   1  1 15713 254 63     192717
[COLOR="Red"]L[/COLOR] Linux Swap           15714   1  1 16078 254 63    5863662
[COLOR="Red"]L[/COLOR] Linux                16079   1  1 16929 254 63   13671252
[COLOR="Red"]L[/COLOR] Linux                16930   0  1 17056 254 63    2040255
[COLOR="Red"]L[/COLOR] Linux                17057   1  1 18340 254 63   20627397
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
```


when i Press  P it shows segmenation fault and exit to the terminal.

You get the segmentation fault because you are using testdisk 6.8; that's why I gave you a link to download the latest stable 6.10 version. You can still use your version to recover the partitions though since it looks like there are fortunately no ghost/invalid partitions to worry about. So using your up/down arrow keys, select each partition, and then use your right/left arrow keys to mark each partition as I have above highlighted in red. If testdisk won't let you mark one or more of the partitions above as "L" that I've shown marked with "L", try marking it with "P" instead. Once you have all the partitions marked exactly as shown above (or marked with P instead of L if necessary), press enter to get the next screen, and then select "write". Then reboot, and post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```

---

### Post by wildman4god on 2009-02-18
Try to restore grub:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

good luck.

---

### Post by ksanthosh77 on 2009-02-22
Thanks for support...

Thanks for your detailed reply, i used the tool: test disk and recovered all the windows partition(happy). rebooted and got grub 22 error,tried some fixing got grub 17 error. finally put fedora got kernel syncing error:unable to mount vfs..../

atlast i put ubuntu hardy(with windows) and happily working.

Thanks for all. how to make it the thread solved?.

---

