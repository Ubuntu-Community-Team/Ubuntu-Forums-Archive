---
title: "[SOLVED] Big problem: Gparted error wrecks partition table"
date: 2008-12-21
forum: General Help
---

### Post by hosed on 2008-12-21
I was running Gparted and it errored out in the middle of moving/resizing partitions. Here's the situation:

/dev/hda1 is a ntfs partition with windows XP on it and windows boots fine.

/dev/hda2 is an old ubuntu installation from when I was too chicken to upgrade without backing everything up first.

/dev/hda3 is a swap, I think.

/dev/hda4 is a logical partition (or maybe it's an extended partition, not quite sure) that should consist of a small FAT32 partition, as well as separate /, /home and /usr partitions for my main ubuntu install (gutsy).

Gutsy won't boot, and I don't know enough about fsck to know what I should be doing to fix this, but the system is currently running one of those live cd linux repair disks. 

I also have an ubuntu live cd, and alternate cd, plus the Gparted live CD that caused the problem in the first place. I can boot into any of these CDs according to what the best move would be.

I certainly appreciate any help anyone could provide as this would be a rather catastrophic problem if I can't recover. I've used Gparted many times and never had a problem, so of course this time i didn't back up. lesson learned. :(

Thanks in advance.

**UPDATE:** I ran cfdisk from the live rescue cd and here is the output:

```
FATAL ERROR: bad logical partition 6. enlarged logical partitions overlap.
```

---

### Post by TheMyself on 2008-12-21
I think you should first port your partition table here(using gparted or XP) so that people can help you.

---

### Post by hosed on 2008-12-21
> **TheMyself said:**
> I think you should first port your partition table here(using gparted or XP) so that people can help you.

Sorry for the screenshot. (Photo of my screen, really.) Best I could do:

[http://img132.imageshack.us/img132/2637/dsc0092bw7.jpg]("http://img132.imageshack.us/img132/2637/dsc0092bw7.jpg")

---

### Post by hosed on 2008-12-21
Sorry, I know posting a link to a photo is lame. I'll just type in the output from testdisk:

```
* HPFS - NTFS 0 1 1 1986 254 63 31921092
L FAT32 LBA 1987 2 1 2241 254  63 4096449 [NO NAME]
L Linux 2242 1 1 5428 254 63 51199092
L Linux 6106 1 1 7635 254 63 24579387
L Linux 7636 1 1 8272 254 63 10233342
P Linux 8273 0 1 9572 254 63 20884500
P Linux Swap 9573 0 1 9278 254 63 2506140
```

---

### Post by hosed on 2008-12-21
Interestingly, testdisk seems to show all the partitions are there and can see the files contained therein. I am therefore hopeful that my data is still recoverable, but I just don't know exactly how to do it and will await any advice anyone may be able to provide. Thanks.

---

### Post by logos34 on 2008-12-21
Looks ok...If you're sure that's what it was before the mishap, and it says "structure ok" at the bottom, select "[Write]" option, and "y" to "write partition table, confirm?".  

It's all explained [here]("http://www.cgsecurity.org/wiki/Menu_Analyse").

---

### Post by hosed on 2008-12-21
> **logos34 said:**
> Looks ok...If you're sure that's what it was before the mishap, and it says "structure ok" at the bottom, select "[Write]" option, and "y" to "write partition table, confirm?".

Thanks for that. I don't know if it's safe to say that I'm "sure," but it looks more or less OK. 

Here is the display from the subsequent screen, which is more illuminating as it lists the partitions in numerical order:

```
1 * HPFS - NTFS 0 1 1 1986 254 63 31921092
2 E extended LBA 1987 0 1 8272 254 63 100984590
3 P Linux 8273 0 1 9572 254 63 20884500
4 P Linux Swap 9573 0 1 9728 254 63 2506140
5 L FAT32 LBA 1987 2 1 2241 254 63 4096449 [NO NAME]
6 L Linux 2242 1 1 5428 254 63 51199092
7 L Linux 6106 1 1 7635 254 63 24579387
8 L Linux 7636 1 1 8272 254 63 10233342
```

It also shows 8 partitions now whereas before it only showed 7. The new one I believe is #2, the Extended partition. 

I am wondering: The E partition ends at sector or block or whatever 8272 which is the same end point as #8. Is this why I got the error about overlap before? Or is this normal for extended partitions that contain logical partitions?

Also, note the gap between where #6 ends (5428 ) and #7 begins (6106). It's the only one that shows a gap, which wasn't there before but seems to represent the state the device was in when this started, i.e., I was in midst of moving and resizing partitions, so a partition was about to be moved over and then resized to fill that gap.

Finally, none of the Linux partitions shows that it is bootable. Do I need to change that?

Thank you very kindly for all your patience and attention. I can't believe I've stayed so calm through this, but it's probably because I knew I could trust in getting good advice here.

---

### Post by caljohnsmith on 2008-12-21
Did you do the "deep search" yet in testdisk? That will give you the best results. How about following these directions if you can (I don't know which testdisk version you are using):
[B]
If you are using Version 6.8:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results.
[B]
If you are using Version 6.9:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results.

Also please post the output of:
```
sudo sfdisk -l
sudo sfdisk -V
```

---

### Post by hosed on 2008-12-21
> **caljohnsmith said:**
> Did you do the "deep search" yet in testdisk? That will give you the best results. How about following these directions if you can (I don't know which testdisk version you are using)
I am using testdisk version 6.4.

> **caljohnsmith said:**
> Also please post the output of:
```
sudo sfdisk -l
```

```
Disk /dev/hda: 9729 cylindersm 25 heads, 63 sectors/track

sfdisk: ERROR: sector 46893735 does not have an msdos signature
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

Device Boot Start End # cyls # blocks ld System
/dev/hda1 * 0+ 1986 1987- 15960546 7 HPFS/NTFS
/dev/hda2   8273 9572 1300 10442250 83 Linux
/dev/hda3   9573 9728 156 1253070 82 Linux swap / Solaris
/dev/hda4   1987 8272 6286 50492295 5 Extended
/dev/hda5   7636+ 8272 637- 5116671 83 Linux
/dev/hda6   6106+ 7635 1530- 12289693+ 83 Linux
```

> **caljohnsmith said:**
> ```
sudo sfdisk -V
```

```
sfdisk: ERROR: sector 46893735 does not have an msdos signature
Warning: partition 5 does not start at a cylinder boundary
```

And I'm about to go and run the deep search in testdisk now and will post output. Sorry for slowness, am having to retype everything from the hosed laptop into the desktop PC which I'm using now to post here. Thanks for your help.

---

### Post by logos34 on 2008-12-21
> **hosed said:**
> It also shows 8 partitions now whereas before it only showed 7. The new one I believe is #2, the Extended partition.

I am wondering: The E partition ends at sector or block or whatever 8272 which is the same end point as #8. Is this why I got the error about overlap before? Or is this normal for extended partitions that contain logical partitions?

Yes, it's fine--the extended contains all the other partitions.  The end of the extended coincides with one of the logicals. Edit: but from what you just posted it appears there's a problem with one of your logical partitions inside.

> 
Also, note the gap between where #6 ends (5428 ) and #7 begins (6106). It's the only one that shows a gap, which wasn't there before but seems to represent the state the device was in when this started, i.e., I was in midst of moving and resizing partitions, so a partition was about to be moved over and then resized to fill that gap.

I assumed it was unallocated space, which is not unusual. If that represents the state gparted left it in when it errored out, you will have to dig down further as I think caljohnsmith says below.

> Finally, none of the Linux partitions shows that it is bootable. Do I need to change that?

The '*' means bootable:

> 1 [COLOR="Red"]*[/COLOR] HPFS - NTFS 0 1 1 1986 254 63 31921092

---

### Post by logos34 on 2008-12-21
Looks like quite a sizeable gap in the front of the extended and where hda6 begins:

inside hda4:

|----empty (1987-6105)----------------hda6 (6106-7635)-----------hda5(7636-8272)---|

/dev/hda4   1987 8272 6286 50492295 5 Extended
/dev/hda5   7636+ 8272 637- 5116671 83 Linux
/dev/hda6   6106+ 7635 1530- 12289693+ 83 Linux

---

### Post by hosed on 2008-12-21
> **caljohnsmith said:**
> Please post the output of the screen that has the deep search results.

Here goes:

```
Disk /dev/hda - 80 GB / 74 GiB - CHS 9729 255 63

Partition       Start       End    Size in sectors
D HPFS - NTFS   0 1  1 1986 254 63 31921092
D HPFS - NTFS   0 1 12 1986 254 63 31921081
L FAT32 LBA  1987 2  1 2241 254 63  4096449 [NO NAME]
L Linux      2242 1  1 5428 254 63 51199092
L Linux      6106 1  1 7635 254 63 24579387
L Linux      7636 1  1 8273 254 63 10233342
* Linux      8273 0  1 9572 254 63 20884500
P Linux Swap 9573 0  1 9728 254 63  2506140

Structure: Ok. Use Left/Right Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable P=Primary L=Logical E=Extended D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files, Enter: to continue
NTFS found using backup sector!, 16GB / 15 GiB
```

Phew!

---

### Post by hosed on 2008-12-21
> **logos34 said:**
> The '*' means bootable:

That's the Windows partition, I thought, which did boot fine last I tried. But now (see my recent post) one of the Linux partitions does show bootable, while the Windows one says it's "D" (deleted).

---

### Post by caljohnsmith on 2008-12-21
OK, it looks like based on your previous results that the first NTFS partition is your Windows partition; please use your up/down arrows though to select each of the linux partitions, and press "p" to get a directory listing. Let us know exactly which of those linux partitions give you a directory listing, and we can work from there.

---

### Post by hosed on 2008-12-21
> **logos34 said:**
> Edit: but from what you just posted it appears there's a problem with one of your logical partitions inside.

That looks like the FAT32 partition which doesn't have anything important on it. I only created it originally before I realized Linux could read and write to the NTFS partition.

testdisk shows this again:

```
1 * HPFS - NTFS 0 1 1 1986 254 63 31921092
2 E extended LBA 1987 0 1 8272 254 63 100984590
3 P Linux 8273 0 1 9572 254 63 20884500
4 P Linux Swap 9573 0 1 9728 254 63 2506140
5 L FAT32 LBA 1987 2 1 2241 254 63 4096449 [NO NAME]
6 L Linux 2242 1 1 5428 254 63 51199092
7 L Linux 6106 1 1 7635 254 63 24579387
8 L Linux 7636 1 1 8272 254 63 10233342
```

NTFS no longer shows "D" for deleted, and Linux partition no longer has bootable "*" beside it.

---

### Post by logos34 on 2008-12-21
you still have a gap between 6 and 7

---

### Post by hosed on 2008-12-21
> **caljohnsmith said:**
> OK, it looks like based on your previous results that the first NTFS partition is your Windows partition; please use your up/down arrows though to select each of the linux partitions, and press "p" to get a directory listing. Let us know exactly which of those linux partitions give you a directory listing, and we can work from there.

According to the directory listings I can see within each partition I have surmised the following:

3 is the old ubuntu installation I mentioned
6 is my / directory
7 is /usr
8 is /home

1 is Windows and 4 is swap, 5 is the FAT32. 2 seems to be the extended partition containing 5, 6, 7 and 8.

---

### Post by hosed on 2008-12-21
> **logos34 said:**
> you still have a gap between 6 and 7

Yes, which makes sense given where Gparted was when it failed. It had just shrunk the Windows partition and was about to move the extended partition over, whereupon it was going to expand my /home partition. That was the reason I was doing this in the first pace, but the error occurred as it was finalizing the move of the extended partition. Looks like that's why the gap is there. I wonder if that makes sense.

---

### Post by logos34 on 2008-12-21
yes, that makes sense--well sort of because the gap looks like its between / and /usr. You didn't mention what partition you were resizing when the error happened. I mentioned it because, once you write it to disk, it's finalized.  

Either that or dig deeper to the state previous to that.

---

### Post by hosed on 2008-12-21
> **logos34 said:**
> yes, that makes sense--well sort of because the gap looks like its between / and /usr. You didn't mention what partition you were resizing when the error happened. I mentioned it because, once you write it to disk, it's finalized.

It had just finished moving a 24GB extended partition to the left, and I'm pretty sure the next step would've been to shrink /usr and use that additional space (plus what I'd previously gained by shrinking the NTFS partition) and then expand /home.

> **logos34 said:**
> Either that or dig deeper to the state previous to that.

I didn't know I could do that.

---

### Post by logos34 on 2008-12-21
> **hosed said:**
> It had just finished moving a 24GB extended partition to the left, and I'm pretty sure the next step would've been to shrink /usr and use that additional space (plus what I'd previously gained by shrinking the NTFS partition) and then expand /home.

I didn't know I could do that.

I meant keep searching deeper, does it give you that option?  For all I know you've reached the end

I'm still not entirely clear on why the gap is appearing between 6 and 7 (/ and /usr) if it was windows you shrank and then grew the extended into the resulting space. If I understand you correctly, you hadn't yet shrunk /usr. I wouldn't want you to write that change and end up with unbootable system.

---

### Post by logos34 on 2008-12-21
Can you mount /home (sda6) on the live cd?  Or is this

> FATAL ERROR: bad logical partition 6. enlarged logical partitions overlap.

preventing that?

if you could save your files then you could reinstall.

---

### Post by hosed on 2008-12-21
> **logos34 said:**
> I'm still not entirely clear on why the gap is appearing between 6 and 7 (/ and /usr) if it was windows you shrank and then grew the extended into the resulting space. If I understand you correctly, you hadn't yet shrunk /usr.
I have a hard time deciphering partition size in GB by looking at the sectors. But /usr was originally about 11 GB and I had planned to resize it to about 7.5 GB. If it's already 7.5 GB, then it had already been shrunk, which explains why the gap is there. How can I derive the GB size from the sector size? Multiply by 1024?

> **logos34 said:**
> I wouldn't want you to write that change and end up with unbootable system.
Thanks for that. :) It is already unbootable, though. But assuming the structure looks ok (EDIT: and also given that I can see that all my directories are there), if I write it to disk, could I later just go and set the bootable flag on the appropriate partition? And by the way, that's the / partition, right? The one to boot from?

---

### Post by hosed on 2008-12-21
> **logos34 said:**
> Can you mount /home (sda6) on the live cd?

Haven't tried that. How would I do that, if you wouldn't mind explaining? Thank you very much for all your help so far. :)

---

### Post by logos34 on 2008-12-21
I meant 'unrecoverable' rather than 'unbootable'. 

* is just a boot flag--more for windows' sake, ubuntu doesn't care about it.  The important thing is that the grub bootloader on the mbr point to ubuntu / -- I guess sda6. 

So is /home mountable?  Because I would advise you to try to backup your files if possible before writing the changes, then if worse comes to worse and it's totally bricked you can reinstall linux (and maybe windows too)

---

### Post by caljohnsmith on 2008-12-21
Before you write a partition table, hosed, please post the output of:
```
sudo sfdisk -d /dev/sda
```
And that will give us an online backup of your current partition table. How about just marking all the linux partitions that gave you a directory listing as L or P (most likely they should all be L), so that you recover all the readable partitions.

---

### Post by logos34 on 2008-12-21
> **hosed said:**
> Haven't tried that. How would I do that, if you wouldn't mind explaining? Thank you very much for all your help so far. :)


sudo mkdir /media/home

sudo mount -t ext3 /dev/sda6 /media/home

(if your on another rescue cd, your already have root priviledges, so you don't need the 'sudo')

cd /media/home

---

### Post by hosed on 2008-12-21
> **caljohnsmith said:**
> Before you write a partition table, hosed, please post the output of:
```
sudo sfdisk -d /dev/sda
```
And that will give us an online backup of your current partition table.

If you mean /dev/hda not /dev/sda, here it is:

```
sfdisk: ERROR: sector 46893735 does not have an msdos signature
# partition table of /dev/hda
unit: sectors

/dev/hda1 : start=       63, size= 31921092, ld= 7, bootable
/dev/hda2 : start=132905745, size= 20884500, ld=83
/dev/hda3 : start=153790245, size=  2506140, ld=82
/dev/hda4 : start= 31921155, size=100984590, ld= 5
/dev/hda5 : start=122672403, size= 10233342, ld=83
/dev/hda6 : start= 98092953, size= 24579387, ld=83
```

> **caljohnsmith said:**
> How about just marking all the linux partitions that gave you a directory listing as L or P (most likely they should all be L), so that you recover all the readable partitions.
I'm not sure I understand what you mean by that. In testdisk I was able to see a directory listing of all the partitions.

---

### Post by hosed on 2008-12-21
> **logos34 said:**
> ...you can reinstall linux (and maybe windows too)
Incidentally, would you believe that the only reason I keep Windows is so that I can plug my iPod into iTunes?

---

### Post by caljohnsmith on 2008-12-21
```

[COLOR="Red"]*[/COLOR] HPFS - NTFS   0 1  1 1986 254 63 31921092
[COLOR="Red"]D[/COLOR] HPFS - NTFS   0 1 12 1986 254 63 31921081
[COLOR="Red"]L[/COLOR] FAT32 LBA  1987 2  1 2241 254 63  4096449 [NO NAME]
[COLOR="Red"]L[/COLOR] Linux      2242 1  1 5428 254 63 51199092
[COLOR="Red"]L[/COLOR] Linux      6106 1  1 7635 254 63 24579387
[COLOR="Red"]L[/COLOR] Linux      7636 1  1 8273 254 63 10233342
[COLOR="Red"]L[/COLOR] Linux      8273 0  1 9572 254 63 20884500
[COLOR="Red"]L[/COLOR] Linux Swap 9573 0  1 9728 254 63  2506140

```
How about marking the partitions as I've shown highlighted in red above; none of the partitions overlap, so you should be fine. If for some reason testdisk won't let you mark one of the "L" partitions above as "L", then use "P" instead. Then press enter to get the next screen where you can write the new partition table. Reboot, and please post the new output of:
```
sudo sfdisk -luS 
sudo fdisk -l
sudo sfdisk -V /dev/hda
```
We can work from there if you want.

---

### Post by hosed on 2008-12-21
I'm going to reboot into the Ubuntu live CD so that I can connect to the network, open Firefox and hopefully get online from the hosed machine and that way I can backup more easily assuming I can mount the hard drive from the live CD. Not to mention making it easier to post my terminal output here. :)

---

### Post by hosed on 2008-12-21
> **caljohnsmith said:**
> How about marking the partitions as I've shown highlighted in red above; none of the partitions overlap, so you should be fine. If for some reason testdisk won't let you mark one of the "L" partitions above as "L", then use "P" instead. Then press enter to get the next screen where you can write the new partition table. Reboot, and please post the new output of:
```
sudo sfdisk -luS 
sudo fdisk -l
sudo sfdisk -V /dev/hda
```
We can work from there if you want.

Ah, I see what you mean. You mean mark them as such in testdisk. They are already marked as L, all except for hda3 (the partition starting at 8273) which is marked P and can't be changed. Are you saying I should go ahead and write the changes?

---

### Post by caljohnsmith on 2008-12-21
Yes, I think you should go ahead and write the changes, and it's OK that the partition starting at 8273 can only be marked as "P". If that's the case though, it looks like your swap partition should also be marked as "P", but use L or P, whichever testdisk will let you use. We have an online backup of your previous partition table, so you should be fine.

---

### Post by hosed on 2008-12-21
> **caljohnsmith said:**
> Yes, I think you should go ahead and write the changes

OK, here I go. Fingers crossed. :o

---

### Post by logos34 on 2008-12-21
good luck to you, hosed...gotta go for now--having some problem with the updates that were in process.

---

### Post by hosed on 2008-12-21
> **caljohnsmith said:**
> Reboot, and please post the new output of:
```
sudo sfdisk -luS 
sudo fdisk -l
sudo sfdisk -V /dev/hda
```
We can work from there if you want.

Yipes, I should've just booted into the Ubuntu live CD from the start, it would've saved me having to retype all the output from the my laptop screen into my desktop PC... Oh well, I've written the changes to disk and now here I am in the live CD from the hosed laptop.

```
ubuntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  31921154   31921092   7  HPFS/NTFS
/dev/sda2      31921155 132905744  100984590   f  W95 Ext'd (LBA)
/dev/sda3     132905745 153790244   20884500  83  Linux
/dev/sda4     153790245 156296384    2506140  82  Linux swap / Solaris
/dev/sda5      31921281  36017729    4096449   c  W95 FAT32 (LBA)
/dev/sda6      36017793  87216884   51199092  83  Linux
/dev/sda7      98092953 122672339   24579387  83  Linux
/dev/sda8     122672403 132905744   10233342  83  Linux

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1987    15960546    7  HPFS/NTFS
/dev/sda2            1988        8273    50492295    f  W95 Ext'd (LBA)
/dev/sda3            8274        9573    10442250   83  Linux
/dev/sda4            9574        9729     1253070   82  Linux swap / Solaris
/dev/sda5            1988        2242     2048224+   c  W95 FAT32 (LBA)
/dev/sda6            2243        5429    25599546   83  Linux
/dev/sda7            6107        7636    12289693+  83  Linux
/dev/sda8            7637        8273     5116671   83  Linux

ubuntu@ubuntu:~$ sudo sfdisk -V /dev/hda
/dev/hda: No such file or directory

sfdisk: cannot open /dev/hda for reading
```

That last one doesn't look too good. What am I doing wrong? Maybe it should be sda instead of hda? If so, the output is:

```
ubuntu@ubuntu:~$ sudo sfdisk -V /dev/sda
/dev/sda: OK
```

Which is a bit more encouraging. What do you think?

---

### Post by caljohnsmith on 2008-12-21
That looks great. How about doing:
```
sudo mkdir /mnt/sda1 /mnt/sda3 /mnt/sda6 /mnt/sda7 /mnt/sda8
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda3 /mnt/sda3
sudo mount /dev/sda6 /mnt/sda6
sudo mount /dev/sda7 /mnt/sda7
sudo mount /dev/sda8 /mnt/sda8
nautilus /mnt &
```
And go through all those mounted partitions in the /mnt directory. Let me know if they all mount OK and if you can access their contents OK.

---

### Post by hosed on 2008-12-22
> **caljohnsmith said:**
> That looks great. How about doing:
```
sudo mkdir /mnt/sda1 /mnt/sda3 /mnt/sda6 /mnt/sda7 /mnt/sda8
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda3 /mnt/sda3
sudo mount /dev/sda6 /mnt/sda6
sudo mount /dev/sda7 /mnt/sda7
sudo mount /dev/sda8 /mnt/sda8
nautilus /mnt &
```
And go through all those mounted partitions in the /mnt directory. Let me know if they all mount OK and if you can access their contents OK.

Yes, they will mount OK and I can access their contents! I've tried booting but am now getting GRUB error 15. Still, I'm feeling quite confident that I've recovered my partitions. I'd be tempted to mark this thread "solved" if only I could actually boot.

But I'll at least lower the threat level from red to orange while I try to sort out the GRUB issue. In the meantime, thank you caljohnsmith and logos34. It's a Christmas miracle! :)

---

### Post by caljohnsmith on 2008-12-22
Are you getting the Grub error before seeing the Grub menu or after you get the menu and select an OS to boot? If it is the former case, how about trying the following to reinstall Grub to the MBR and point it to the correct partition for its boot files:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,5), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If you have problems booting any of the OSes from the Grub menu, that should be easy for us to fix by tweaking your Ubuntu menu.lst. If you would like any help with that, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your new partitioning setup and what the problem might be.

---

### Post by hosed on 2008-12-22
> **caljohnsmith said:**
> Are you getting the Grub error before seeing the Grub menu or after you get the menu and select an OS to boot?

It's after I select an OS to boot, and only if I select Ubuntu. Windows boots fine.

> **caljohnsmith said:**
> If you have problems booting any of the OSes from the Grub menu, that should be easy for us to fix by tweaking your Ubuntu menu.lst.

My menu.lst is a mess, and not the least of it being the fact that when I recently upgraded from Feisty to Gutsy, my GRUB menu never changed to show the new Ubuntu 7.10, kernel 2.6.22-16-386, but continued to show kernel 2.6.20-16-386 at the top.

> **caljohnsmith said:**
> If you would like any help with that, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your new partitioning setup and what the problem might be.

Here it is:

```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #3 for its boot files.

sda1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 63.
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /ntdetect.com

sda2:
    File system:  Extended Partition

sda3:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 6.06.1 LTS \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4:
    File system:  swap

sda5:
    File system:  vfat
    Boot sector  type:  Fat
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda6:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Ubuntu 7.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda8:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31921154    15960546    7  HPFS/NTFS
/dev/sda2        31921155   132905744    50492295    f  W95 Ext'd (LBA)
/dev/sda3       132905745   153790244    10442250   83  Linux
/dev/sda4       153790245   156296384     1253070   82  Linux swap / Solaris
/dev/sda5        31921281    36017729     2048224+   c  W95 FAT32 (LBA)
/dev/sda6   *    36017793    87216884    25599546   83  Linux
/dev/sda7        87216948   102815999     7799526   83  Linux
/dev/sda8       102816063   132905744    15044841   83  Linux

Warning: usually one can boot from primary partitions only
LILO disregards the `bootable' flag.
/dev/sda: OK

/dev/sda1: UUID="CF911457D97E0CC" TYPE="ntfs" 
/dev/sda3: UUID="1072eaff-ce25-4573-8a7e-7ec6c4be3dbe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="fb5dfd4d-8017-4791-b9e4-e93a99a81c05" 
/dev/sda5: UUID="46F8-9DFD" TYPE="vfat" 
/dev/sda6: UUID="cd5065a9-a9f6-4a96-a738-e5db11597923" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="f2c75b55-4e65-4932-ae8f-31dc3da0d7fd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="403d5900-61b1-461d-8688-68c603536e33" SEC_TYPE="ext2" TYPE="ext3" 

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


sda3/boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.17-12-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386
savedefault

title		Ubuntu, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro single
initrd		/boot/initrd.img-2.6.17-12-386

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-686 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-686 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-686 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-686 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-26-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda3/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4       /media/hda4     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

sda3/boot

total 46104
drwxr-xr-x  3 root root    4096 2007-07-20 19:32 .
drwxr-xr-x 25 root root    4096 2007-09-25 03:07 ..
-rw-r--r--  1 root root  266735 2006-09-08 21:51 abi-2.6.15-26-386
-rw-r--r--  1 root root  266735 2006-12-08 19:34 abi-2.6.15-27-386
-rw-r--r--  1 root root  265897 2006-12-08 19:35 abi-2.6.15-27-686
-rw-r--r--  1 root root  266735 2007-07-18 23:36 abi-2.6.15-28-386
-rw-r--r--  1 root root  265897 2007-07-18 23:39 abi-2.6.15-28-686
-rw-r--r--  1 root root   69978 2006-09-08 19:52 config-2.6.15-26-386
-rw-r--r--  1 root root   69967 2006-12-08 17:50 config-2.6.15-27-386
-rw-r--r--  1 root root   69815 2006-12-08 17:57 config-2.6.15-27-686
-rw-r--r--  1 root root   69967 2007-07-18 22:49 config-2.6.15-28-386
-rw-r--r--  1 root root   69815 2007-07-18 22:56 config-2.6.15-28-686
drwxr-xr-x  2 root root    4096 2007-09-26 02:05 grub
-rw-r--r--  1 root root 6775109 2006-11-02 00:40 initrd.img-2.6.15-26-386
-rw-r--r--  1 root root 6775985 2006-12-19 07:10 initrd.img-2.6.15-27-386
-rw-r--r--  1 root root 6972763 2007-01-24 00:07 initrd.img-2.6.15-27-686
-rw-r--r--  1 root root 6778103 2007-07-20 19:34 initrd.img-2.6.15-28-386
-rw-r--r--  1 root root 6974264 2007-07-20 19:35 initrd.img-2.6.15-28-686
-rw-r--r--  1 root root   94760 2005-10-25 10:32 memtest86+.bin
-rw-r--r--  1 root root  726461 2006-09-08 21:51 System.map-2.6.15-26-386
-rw-r--r--  1 root root  725967 2006-12-08 19:34 System.map-2.6.15-27-386
-rw-r--r--  1 root root  735504 2006-12-08 19:35 System.map-2.6.15-27-686
-rw-r--r--  1 root root  727165 2007-07-18 23:36 System.map-2.6.15-28-386
-rw-r--r--  1 root root  736702 2007-07-18 23:39 System.map-2.6.15-28-686
-rw-r--r--  1 root root 1414735 2006-09-08 21:51 vmlinuz-2.6.15-26-386
-rw-r--r--  1 root root 1414752 2006-12-08 19:34 vmlinuz-2.6.15-27-386
-rw-r--r--  1 root root 1516100 2006-12-08 19:35 vmlinuz-2.6.15-27-686
-rw-r--r--  1 root root 1415298 2007-07-18 23:36 vmlinuz-2.6.15-28-386
-rw-r--r--  1 root root 1516164 2007-07-18 23:39 vmlinuz-2.6.15-28-686

sda3/boot/grub

total 212
drwxr-xr-x 2 root root   4096 2007-09-26 02:05 .
drwxr-xr-x 3 root root   4096 2007-07-20 19:32 ..
-rw-r--r-- 1 root root    197 2006-10-31 07:03 default
-rw-r--r-- 1 root root     15 2006-10-31 07:03 device.map
-rw-r--r-- 1 root root   7508 2006-10-31 07:03 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2006-10-31 07:03 fat_stage1_5
-rw-r--r-- 1 root root   8128 2006-10-31 07:03 jfs_stage1_5
-rw-r--r-- 1 root root   5400 2007-07-20 19:35 menu_lst
-rw-r--r-- 1 root root   8495 2007-09-26 05:17 menu.lst
-rw-r--r-- 1 root root   5400 2007-07-20 19:35 menu.lst~
-rw-r--r-- 1 root root   6804 2006-10-31 07:03 minix_stage1_5
-rw-r--r-- 1 root root   9076 2006-10-31 07:03 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2006-10-31 07:03 stage1
-rw-r--r-- 1 root root 105428 2006-10-31 07:03 stage2
-rw-r--r-- 1 root root   8764 2006-10-31 07:03 xfs_stage1_5

sda6/boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-16-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-386

title		Ubuntu 7.10, kernel 2.6.22-16-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro single
initrd		/boot/initrd.img-2.6.22-16-386

title		Ubuntu 7.10, kernel 2.6.20-17-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-17-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro quiet splash
initrd		/boot/initrd.img-2.6.20-17-386

title		Ubuntu 7.10, kernel 2.6.20-17-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-17-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro single
initrd		/boot/initrd.img-2.6.20-17-386

title		Ubuntu 7.10, kernel 2.6.20-16-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.17-12-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386

title		Ubuntu 7.10, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro single
initrd		/boot/initrd.img-2.6.17-12-386

title		Ubuntu 7.10, kernel 2.6.15-26-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 7.10, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-686 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-686 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-686 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-686 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-26-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda6/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8 -- converted during upgrade to edgy
UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=403d5900-61b1-461d-8688-68c603536e33 /home ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=0CF911457D97E0CC /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=1072eaff-ce25-4573-8a7e-7ec6c4be3dbe /media/hda2 ext3 defaults 0 2
# /dev/hda7 -- converted during upgrade to edgy
UUID=f2c75b55-4e65-4932-ae8f-31dc3da0d7fd /usr ext3 defaults 0 2
# /dev/hda3 -- converted during upgrade to edgy
UUID=6133a92c-5a0b-4005-84ae-7a423cadda5c none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
# added this to get printer to work

sda6/boot

total 85044
drwxr-xr-x  3 root root    4096 2008-12-12 23:53 .
drwxr-xr-x 23 root root   24576 2008-12-20 03:20 ..
-rw-r--r--  1 root root  266735 2006-08-03 05:09 abi-2.6.15-26-386
-rw-r--r--  1 root root  286242 2007-07-16 19:52 abi-2.6.17-12-386
-rw-r--r--  1 root root  411070 2008-02-12 06:11 abi-2.6.20-16-386
-rw-r--r--  1 root root  411070 2008-08-20 17:19 abi-2.6.20-17-386
-rw-r--r--  1 root root  420831 2008-11-24 21:42 abi-2.6.22-16-386
-rw-r--r--  1 root root   69903 2006-08-03 02:49 config-2.6.15-26-386
-rw-r--r--  1 root root   75289 2007-07-16 17:47 config-2.6.17-12-386
-rw-r--r--  1 root root   83252 2008-02-12 02:02 config-2.6.20-16-386
-rw-r--r--  1 root root   83252 2008-08-20 14:14 config-2.6.20-17-386
-rw-r--r--  1 root root   75380 2008-11-24 21:42 config-2.6.22-16-386
drwxr-xr-x  2 root root    4096 2008-12-12 23:48 grub
-rw-r--r--  1 root root 7128619 2007-07-30 11:00 initrd.img-2.6.15-26-386
-rw-r--r--  1 root root 8208437 2007-07-31 06:43 initrd.img-2.6.17-12-386
-rw-r--r--  1 root root 6806158 2007-07-31 06:14 initrd.img-2.6.17-12-386.bak
-rw-r--r--  1 root root 8249874 2008-02-15 01:48 initrd.img-2.6.20-16-386
-rw-r--r--  1 root root 8249956 2008-02-04 18:11 initrd.img-2.6.20-16-386.bak
-rw-r--r--  1 root root 8562864 2008-12-12 22:26 initrd.img-2.6.20-17-386
-rw-r--r--  1 root root 8250321 2008-08-28 02:08 initrd.img-2.6.20-17-386.bak
-rw-r--r--  1 root root 8582458 2008-12-12 23:53 initrd.img-2.6.22-16-386
-rw-r--r--  1 root root 8582879 2008-12-12 23:48 initrd.img-2.6.22-16-386.bak
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  726461 2006-08-03 05:09 System.map-2.6.15-26-386
-rw-r--r--  1 root root  714837 2007-07-16 19:52 System.map-2.6.17-12-386
-rw-r--r--  1 root root  789196 2008-02-12 06:13 System.map-2.6.20-16-386
-rw-r--r--  1 root root  789222 2008-08-20 17:20 System.map-2.6.20-17-386
-rw-r--r--  1 root root  803865 2008-11-24 21:42 System.map-2.6.22-16-386
-rw-r--r--  1 root root 1414781 2006-08-03 05:09 vmlinuz-2.6.15-26-386
-rw-r--r--  1 root root 1574274 2007-07-16 19:52 vmlinuz-2.6.17-12-386
-rw-r--r--  1 root root 1678348 2008-02-12 06:11 vmlinuz-2.6.20-16-386
-rw-r--r--  1 root root 1679020 2008-08-20 17:19 vmlinuz-2.6.20-17-386
-rw-r--r--  1 root root 1695000 2008-11-24 21:42 vmlinuz-2.6.22-16-386

sda6/boot/grub

total 208
drwxr-xr-x 2 root root   4096 2008-12-12 23:48 .
drwxr-xr-x 3 root root   4096 2008-12-12 23:53 ..
-rw-r--r-- 1 root root    197 2007-07-30 07:26 default
-rw-r--r-- 1 root root     15 2007-07-30 07:26 device.map
-rw-r--r-- 1 root root   7508 2007-07-30 07:26 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2007-07-30 07:26 fat_stage1_5
-rw-r--r-- 1 root root   8128 2007-07-30 07:26 jfs_stage1_5
-rw-r--r-- 1 root root   9396 2008-12-12 23:48 menu.lst
-rw-r--r-- 1 root root   8998 2008-12-12 23:48 menu.lst~
-rw-r--r-- 1 root root   6804 2007-07-30 07:26 minix_stage1_5
-rw-r--r-- 1 root root   9076 2007-07-30 07:26 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-07-30 07:26 stage1
-rw-r--r-- 1 root root 105428 2007-07-30 07:26 stage2
-rw-r--r-- 1 root root   8764 2007-07-30 07:26 xfs_stage1_5

StdErr Messages 

Unknown BootLoader  on /dev/sda6

00000000  fe 2d bb bf e2 7b 24 5a  7d 94 7f 05 e5 06 4c d0  |.-...{$Z}.....L.|
00000010  b7 c3 b5 fb e5 b8 64 dd  e3 e0 f9 e3 3c ce e8 2d  |......d.....<..-|
00000020  92 e5 f3 7b f5 1e 3a f8  af cf c6 85 e6 8e a3 7e  |...{..:........~|
00000030  00 e5 b1 e4 ca 47 f3 5a  f0 b2 cf 4d af 17 2d 97  |.....G.Z...M..-.|
00000040  9e c1 76 9c 17 ca 29 2e  f3 76 96 ca 79 2d 1f 37  |..v...)..v..y-.7|
00000050  b3 81 a5 5a 20 bb 1c 6b  a8 dd 71 5f 2d f0 fb b7  |...Z ..k..q_-...|
00000060  4e 5e ba d3 c1 59 0e 16  32 14 cc 2c 02 b9 05 ac  |N^...Y..2..,....|
00000070  10 2c 95 7a 5d af 57 12  00 1e 5c af ff 3b bb d6  |.,.z].W...\..;..|
00000080  6d a1 10 cc 13 a1 58 9d  f3 14 7b 51 10 f4 75 a7  |m.....X...{Q..u.|
00000090  b7 59 46 02 47 3a 1b ca  72 8f e6 77 a7 99 a4 e4  |.YF.G:..r..w....|
000000a0  68 d6 d5 10 34 d3 95 5f  d6 71 49 7c f7 8a ee ba  |h...4.._.qI|....|
000000b0  b4 3d 4b a5 9d bc 15 0b  f0 59 e4 69 a3 74 a1 83  |.=K......Y.i.t..|
000000c0  2f 89 a7 9b 0c c4 af 68  ba f8 7c 15 4b 6e 41 f8  |/......h..|.KnA.|
000000d0  bc 07 5b 88 97 4b 7c e3  eb 55 d3 bb 75 71 d5 4b  |..[..K|..U..uq.K|
000000e0  4a 11 fc 44 d5 84 6f ca  82 d2 cf 2a cc c8 b5 f0  |J..D..o....*....|
000000f0  c1 c0 aa 0c 00 96 8b 96  15 d5 78 c7 9f 8a 68 b8  |..........x...h.|
00000100  21 0c 09 b5 0c 00 00 0f  3d 5d 29 90 e2 43 99 45  |!.......=])..C.E|
00000110  60 50 02 06 9d 9a 03 5a  ae b5 34 4b 6a 50 12 f3  |`P.....Z..4KjP..|
00000120  d1 22 3a fa ac 7b ed 24  a4 8f a8 2e a5 bb 0a aa  |.":..{.$........|
00000130  06 9a a4 3e fb a6 4c 43  40 da 76 be c2 60 09 f5  |...>..LC@.v..`..|
00000140  92 b3 05 84 68 89 dc f9  ea ab 2b d1 55 91 14 0e  |....h.....+.U...|
00000150  d1 85 13 69 e7 ae 58 37  a9 d9 fa f4 db e6 98 95  |...i..X7........|
00000160  ce 3a f9 03 af e1 d6 b7  0b d6 e2 94 f4 ae 15 d2  |.:..............|
00000170  ea 4d e7 17 22 5f 5f 97  35 ec 52 fc 24 e4 e8 b2  |.M.."__.5.R.$...|
00000180  38 92 68 86 99 52 93 a5  6d 18 c1 53 93 c9 57 93  |8.h..R..m..S..W.|
00000190  4e a8 e0 cd 20 98 80 61  08 a4 47 7c de 6c 9a c9  |N... ..a..G|.l..|
000001a0  71 25 09 f3 29 5a 38 c1  aa 77 d0 d8 89 4d 4b 64  |q%..)Z8..w...MKd|
000001b0  a9 48 4a 13 20 b0 08 d8  0d 14 ba 0d 35 8b d1 73  |.HJ. .......5..s|
000001c0  52 ed 11 31 42 54 d7 cf  83 3c aa a4 0a 97 12 c4  |R..1BT...<......|
000001d0  0d 00 49 10 02 13 d2 b8  38 c4 f5 ad 91 a4 e3 a0  |..I.....8.......|
000001e0  39 eb 47 2a c3 1a b1 be  74 7a 8a 77 45 42 cc c0  |9.G*....tz.wEB..|
000001f0  34 a4 14 8e a6 0e 9f 45  df 79 be f7 1e e8 8a 9a  |4......E.y......|
00000200

Unknown BootLoader  on /dev/sda7

00000000  74 00 69 00 76 00 65 00  20 00 69 00 64 00 65 00  |t.i.v.e. .i.d.e.|
00000010  6e 00 74 00 69 00 66 00  69 00 65 00 72 00 73 00  |n.t.i.f.i.e.r.s.|
00000020  2e 00 0d 00 0a 00 00 00  dc 00 01 00 54 00 68 00  |............T.h.|
00000030  65 00 20 00 72 00 65 00  71 00 75 00 65 00 73 00  |e. .r.e.q.u.e.s.|
00000040  74 00 65 00 64 00 20 00  6f 00 70 00 65 00 72 00  |t.e.d. .o.p.e.r.|
00000050  61 00 74 00 69 00 6f 00  6e 00 20 00 64 00 69 00  |a.t.i.o.n. .d.i.|
00000060  64 00 20 00 6e 00 6f 00  74 00 20 00 73 00 61 00  |d. .n.o.t. .s.a.|
00000070  74 00 69 00 73 00 66 00  79 00 20 00 6f 00 6e 00  |t.i.s.f.y. .o.n.|
00000080  65 00 20 00 6f 00 72 00  20 00 6d 00 6f 00 72 00  |e. .o.r. .m.o.r.|
00000090  65 00 20 00 63 00 6f 00  6e 00 73 00 74 00 72 00  |e. .c.o.n.s.t.r.|
000000a0  61 00 69 00 6e 00 74 00  73 00 20 00 61 00 73 00  |a.i.n.t.s. .a.s.|
000000b0  73 00 6f 00 63 00 69 00  61 00 74 00 65 00 64 00  |s.o.c.i.a.t.e.d.|
000000c0  20 00 77 00 69 00 74 00  68 00 20 00 74 00 68 00  | .w.i.t.h. .t.h.|
000000d0  65 00 20 00 63 00 6c 00  61 00 73 00 73 00 20 00  |e. .c.l.a.s.s. .|
000000e0  6f 00 66 00 20 00 74 00  68 00 65 00 20 00 6f 00  |o.f. .t.h.e. .o.|
000000f0  62 00 6a 00 65 00 63 00  74 00 2e 00 0d 00 0a 00  |b.j.e.c.t.......|
00000100  00 00 00 00 ac 00 01 00  54 00 68 00 65 00 20 00  |........T.h.e. .|
00000110  64 00 69 00 72 00 65 00  63 00 74 00 6f 00 72 00  |d.i.r.e.c.t.o.r.|
00000120  79 00 20 00 73 00 65 00  72 00 76 00 69 00 63 00  |y. .s.e.r.v.i.c.|
00000130  65 00 20 00 63 00 61 00  6e 00 20 00 70 00 65 00  |e. .c.a.n. .p.e.|
00000140  72 00 66 00 6f 00 72 00  6d 00 20 00 74 00 68 00  |r.f.o.r.m. .t.h.|
00000150  65 00 20 00 72 00 65 00  71 00 75 00 65 00 73 00  |e. .r.e.q.u.e.s.|
00000160  74 00 65 00 64 00 20 00  6f 00 70 00 65 00 72 00  |t.e.d. .o.p.e.r.|
00000170  61 00 74 00 69 00 6f 00  6e 00 20 00 6f 00 6e 00  |a.t.i.o.n. .o.n.|
00000180  6c 00 79 00 20 00 6f 00  6e 00 20 00 61 00 20 00  |l.y. .o.n. .a. .|
00000190  6c 00 65 00 61 00 66 00  20 00 6f 00 62 00 6a 00  |l.e.a.f. .o.b.j.|
000001a0  65 00 63 00 74 00 2e 00  0d 00 0a 00 00 00 00 00  |e.c.t...........|
000001b0  fc 00 01 00 54 00 68 00  65 00 20 00 64 00 69 00  |....T.h.e. .d.i.|
000001c0  72 00 65 00 63 00 74 00  6f 00 72 00 79 00 20 00  |r.e.c.t.o.r.y. .|
000001d0  73 00 65 00 72 00 76 00  69 00 63 00 65 00 20 00  |s.e.r.v.i.c.e. .|
000001e0  63 00 61 00 6e 00 6e 00  6f 00 74 00 20 00 70 00  |c.a.n.n.o.t. .p.|
000001f0  65 00 72 00 66 00 6f 00  72 00 6d 00 20 00 74 00  |e.r.f.o.r.m. .t.|
00000200

Unknown BootLoader  on /dev/sda8

00000000  80 7e 23 80 21 0c 14 fd  a6 9f 08 65 08 c0 60 05  |.~#.!......e..`.|
00000010  28 50 b6 15 77 1a 2e 4b  b9 2e 5d 03 de 72 20 18  |(P..w..K..]..r .|
00000020  16 56 6b ea b9 bf 36 2b  ea dd 88 89 24 f8 21 64  |.Vk...6+....$.!d|
00000030  69 34 52 d1 1e 47 f7 47  c7 c9 e4 cc be ef ef eb  |i4R..G.G........|
00000040  63 26 4d e7 1b 4d cb 65  a6 cb aa cc 4d 87 2f 4c  |c&M..M.e....M./L|
00000050  75 ea 83 40 e5 53 6f 6c  53 6c aa 81 b9 e3 a4 a9  |u..@.SolSl......|
00000060  e3 1b ab a8 2d 1a a6 5c  36 8d 41 25 87 5d 99 35  |....-..\6.A%.].5|
00000070  3d 1b ca 56 f2 2f 90 8d  8a b0 82 6b 74 84 36 60  |=..V./.....kt.6`|
00000080  f8 07 09 a4 20 dd 39 34  27 ad 8e 8d 9b aa e4 5d  |.... .94'......]|
00000090  a0 37 cd 31 b7 a2 5d d4  00 b1 5f 99 51 85 27 e9  |.7.1..]..._.Q.'.|
000000a0  b5 2e 40 4d 47 29 54 77  2e 3c bb be 24 9d 6c c2  |..@MG)Tw.<..$.l.|
000000b0  56 c9 5d a2 34 65 a6 85  e5 53 ae 8c a6 65 56 bf  |V.].4e...S...eV.|
000000c0  41 a4 85 19 9a 17 14 c2  fa 11 1a 64 eb bb 8e dd  |A..........d....|
000000d0  26 22 19 c7 6d 0d fe 8a  d8 b1 4d 19 dc bb 35 95  |&"..m.....M...5.|
000000e0  15 f0 d7 20 51 55 c7 09  b6 4c 47 d3 54 af 82 02  |... QU...LG.T...|
000000f0  44 de 2b 4f 39 6b 94 ce  9e 9f fb 94 b2 65 3b 6c  |D.+O9k.......e;l|
00000100  7c ce be f8 a9 79 71 6e  aa ed 61 2a 7c 21 6d aa  ||....yqn..a*|!m.|
00000110  9c 59 c0 ee 9c af 96 c5  36 5a 5a 2b a4 e4 8e 41  |.Y......6ZZ+...A|
00000120  64 d2 d0 b0 1d 96 64 cd  5e 34 69 5c 5c 88 8e bb  |d.....d.^4i\\...|
00000130  d1 b0 d8 0a 27 93 6d 77  82 ce e6 01 60 15 b0 46  |....'.mw....`..F|
00000140  72 52 02 81 23 71 30 69  e4 f4 43 51 32 e0 2b 44  |rR..#q0i..CQ2.+D|
00000150  61 f7 00 c1 0e 21 0c 14  ed ca 8f 0d 62 88 80 60  |a....!......b..`|
00000160  c1 ad 80 35 55 45 c4 96  b9 25 c9 72 e8 29 5e 48  |...5UE...%.r.)^H|
00000170  26 e8 bc 43 b0 b3 7d ba  5e 82 49 d0 f2 e0 2c bc  |&..C..}.^.I...,.|
00000180  e3 f6 f9 e6 fa ce e2 96  83 22 2a e9 14 e6 38 d5  |........."*...8.|
00000190  d5 61 bc 7c e4 ab 67 98  8c c7 4e f2 a7 2a f0 5b  |.a.|..g...N..*.[|
000001a0  06 aa 56 ef b6 e4 60 c7  f6 c6 0b 03 a9 75 9c 3e  |..V...`......u.>|
000001b0  2f d3 99 99 fe b7 c7 93  e2 29 67 51 e4 57 d8 a7  |/........)gQ.W..|
000001c0  d7 da 26 77 f0 d0 18 66  93 0d 50 d5 60 2d 9e 85  |..&w...f..P.`-..|
000001d0  ec bb c2 76 97 2d 8e a5  d0 a4 41 ba b0 ed 4c 61  |...v.-....A...La|
000001e0  9e 34 99 4d f1 8f 1c fd  66 04 ea 0b cd e1 e4 f4  |.4.M....f.......|
000001f0  de d0 a3 46 2c 9e ad a6  7d 2c 12 a1 94 fe d3 c1  |...F,...},......|
00000200

umount: /tmp/BootInfo/sda5: device is busy
umount: /tmp/BootInfo/sda5: device is busy
```

---

### Post by caljohnsmith on 2008-12-22
OK, when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hd0,6)", press "e" to edit it, change it to "root (hd0,5)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot your Ubuntu 7.10. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

But according to the script you ran, you have Ubuntu 6.06 in the sda3 partition, while Ubuntu 7.10 is in sda6. What is your ultimate goal? Which Ubuntu version do you want to keep?

---

### Post by hosed on 2008-12-22
> **caljohnsmith said:**
> But according to the script you ran, you have Ubuntu 6.06 in the sda3 partition, while Ubuntu 7.10 is in sda6. What is your ultimate goal? Which Ubuntu version do you want to keep?
Well, I want to *keep* them both, for now, anyway, but I only ever need to *boot* 7.10.

> **caljohnsmith said:**
> OK, when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hd0,6)", press "e" to edit it, change it to "root (hd0,5)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot your Ubuntu 7.10. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.
OK, I'm off to try this. Thanks again!

---

### Post by hosed on 2008-12-22
> **caljohnsmith said:**
>  you'll need to modify your menu.lst to make it permanent

Wow, thank you so much. I am able to boot into Ubuntu 7.10 again and everything is as it was. Actually, using Gparted on the the live CD, I was also able to complete the resizing of the partitions I was originally attempting to do when all the trouble started. So now all I have to do is make the changes to GRUB permanent.

I've modified the menu.lst file to change (hd0,6) to (hd0,5) and commented out all the other OSes that I don't need. But when I reboot the changes aren't there, so I assume there's another step required to write the new menu.lst to the MBR? Probably running update-grub or grub-install, but I don't know which.

This is so cool. Thank you.

---

### Post by caljohnsmith on 2008-12-22
You're right, Grub in the MBR Is currently controlled by your Ubuntu 6.06 partition, so to give 7.10 control you can do:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
And then you should get the 7.10 Grub menu on start up. Let me know how it goes. :)

---

### Post by hosed on 2008-12-22
> **caljohnsmith said:**
> You're right, Grub in the MBR Is currently controlled by your Ubuntu 6.06 partition, so to give 7.10 control you can do:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
And then you should get the 7.10 Grub menu on start up. Let me know how it goes. :)

Yes, I got the nice, tidy new GRUB menu and selected 7.10 and it started to boot but then I got the following message cascading down my screen many times per second:

```
device-mapper: table: 254.6: linear: dm-linear: Device lookup failed.
```

So I'm back to the live CD. :(

---

### Post by caljohnsmith on 2008-12-22
It looks like that might be an issue with the particular kernel you booted. How about instead trying "Ubuntu 7.10, kernel 2.6.20-16-386" from the Grub menu on start up and let me know if that works.

---

### Post by hosed on 2008-12-22
> **caljohnsmith said:**
> It looks like that might be an issue with the particular kernel you booted. How about instead trying "Ubuntu 7.10, kernel 2.6.20-16-386" from the Grub menu on start up and let me know if that works.

So it looks like I'm able to boot into the Ubuntu 7.10, kernel 2.6.20-16-386 kernel, which is what I was doing before, so I would say that for the purposes of this thread, my original problem is solved. Thank you, caljohnsmith! I should send you a Christmas turkey. :)

---

### Post by caljohnsmith on 2008-12-22
> **hosed said:**
> So it looks like I'm able to boot into the Ubuntu 7.10, kernel 2.6.20-16-386 kernel, which is what I was doing before, so I would say that for the purposes of this thread, my original problem is solved. Thank you, caljohnsmith! I should send you a Christmas turkey. :)
You're certainly welcome, hosed, and of course a big kudos goes to logos34 and all his help too. Cheers and have fun with your Ubuntu installs, and hopefully you won't run into any more major problems. :)

---

