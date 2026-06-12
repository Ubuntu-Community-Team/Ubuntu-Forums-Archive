---
title: "boot problem"
date: 2009-06-10
forum: General Help
---

### Post by DeViLDuD3 on 2009-06-10
well I had ubuntu 8.10 installed along with win xp, recently my win xp got crashed so I formatted the C: drive and installed win vista, no the problem is I already have installed ubuntu 8.10 and I dont know how to load it back, I tried to boot it with auto grub disk, but it gave some error like vmlinuz ( along file name ) not found.. 
so any solutions for this ?

---

### Post by DeViLDuD3 on 2009-06-10
anyone :O ?

---

### Post by blueridgedog on 2009-06-10
If you reinstall an MS os, it overwrites your master boot record, and you can not boot Ubuntu.  The process to restore grub to your MBR is as follows:


Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will result in a "grub>" prompt. At grub>. enter these commands
```

find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to use as the source for the new mbr.

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Note, if you want to put the new mbr in another hard drive, you will need to adjust it accordingly.

Finally exit the grub shell
```

quit
```

---

### Post by DeViLDuD3 on 2009-06-10
thanx alot bro.,. no many ppl reply here :S

---

### Post by DeViLDuD3 on 2009-06-13
ok It didnt solved the problem either, the installer menu is being showed at the boot menu :s what should Ido next? format the whole ubuntu partition and install it freshly over windows? or is there a way out ?

---

### Post by statistic on 2009-06-13
Do you mean the Live cd installer menu?

---

### Post by DeViLDuD3 on 2009-06-14
yes that is rite, it shows me like 4-5 options start live cd or install with (something) install with (something) the auto grub doesnt show the menu it previously used to show like start linux generic kernel 2.6. something and memtest 3 options alltogether, how do I fix this?

---

### Post by DeViLDuD3 on 2009-06-14
hulo?

---

### Post by twright on 2009-06-14
Hi,
[blueridgedog]("http://ubuntuforums.org/member.php?u=459469")'s advice is how I usually reinstall grub and I don't see why it would not work. Can you boot into try Ubuntu mode on the live cd, rerun his commands in terminal and copy and paste all of the output from terminal here as to give a better picture of what is going wrong?

---

### Post by AndyCee on 2009-06-14
> **DeViLDuD3 said:**
> yes that is rite, it shows me like 4-5 options start live cd or install with (something) install with (something) the auto grub doesnt show the menu it previously used to show like start linux generic kernel 2.6. something and memtest 3 options alltogether, how do I fix this?

That's the menu for booting into a liveCD. Don't mean to ask the obvious - but have you taken the CD out?

If you select "Boot from hard-drive" from that menu, and it takes you straight to windows, then grub hasn't been installed successfully.

---

### Post by blueridgedog on 2009-06-14
> **DeViLDuD3 said:**
> yes that is rite, it shows me like 4-5 options start live cd or install with (something) install with (something) the auto grub doesnt show the menu it previously used to show like start linux generic kernel 2.6. something and memtest 3 options alltogether, how do I fix this?

Go ahead and boot into the live CD (try Ubuntu I think is what it is called).  Once you are into a Ubuntu session on the cd, bring up a terminal, Applications -> Accessories -> Terminal, then enter the commands I posted for you.

---

### Post by DeViLDuD3 on 2009-06-15
ok the auto super grub disk menu gives me the following options (the ubuntu cd is not in the cdrom)
 
start installer in normal mode
start installer in safe graphics mode
start installer with ACPI workarounds
start installler in verbose mode
Read-only (Live CD Desktop)
 
 
anyways when I select the livecd option, and used the following command in terminal :
 
 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo fdisk -l
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9cf89cf8
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1147     9213246   83  Linux
/dev/sda2            1148        4864    29856802+   f  W95 Ext'd (LBA)
/dev/sda5            1148        2422    10241406    b  W95 FAT32
/dev/sda6            2423        3697    10241406    b  W95 FAT32
/dev/sda7            3698        4864     9373896    b  W95 FAT32
Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d289d28
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        9714    37069987+   f  W95 Ext'd (LBA)
/dev/sdb5            5100        7394    18434556   83  Linux
/dev/sdb6            7395        9714    18635368+   b  W95 FAT32
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] 

 
 
I just know the my Ubuntu linux was installed in a 17 gb partition and I had another partition coverted to linux filesystem, that makes two linux partitions as showed above
 
does /dev/sda1   *  means that linux is picking up the boot from this partition?
whatever, I know that the 80 gb is distributed in 3 partitions, one 40gb NTFS in which my windows Vista is installed, the other is 20 gb which is used in fat32 and showed in windows, the other one is where my linux is installed which is not showed in windows...
 
any more clues?

---

### Post by twright on 2009-06-16
with that info you should just be able to use these commands unmodified in terminal to fit it:
```

sudo grub
root (hd0,0)
setup (hd0)
quit

```

---

### Post by DeViLDuD3 on 2009-06-17
kk ill try

---

### Post by twright on 2009-06-17
> **DeViLDuD3 said:**
> kk ill try
Good luck,
if it does not work please copy and paste the output here :-)

---

### Post by martin_legion on 2009-06-17
You can try Super Grub Disk.
It tries to fix GRUB in many ways

Good luck

---

### Post by DeViLDuD3 on 2009-06-18
ok this grub thing wuz done before too...
and it did the same
again its showin the same menu in auto grub super disk menu
 
start installer in normal mode
start installer in safe graphics mode
start installer with ACPI workarounds
start installler in verbose mode
Read-only (Live CD Desktop)

 
still same :s therez something that makes me curious, why does * being showed at a drive which doesnt have linux in it ? since my linux is installed in 17 gb partition in 80 gb hard disk,, does it has something to do with it ?

---

### Post by DeMus on 2009-06-18
> **DeViLDuD3 said:**
> ok this grub thing wuz done before too...
and it did the same
again its showin the same menu in auto grub super disk menu
 
start installer in normal mode
start installer in safe graphics mode
start installer with ACPI workarounds
start installler in verbose mode
Read-only (Live CD Desktop)

 
still same :s therez something that makes me curious, why does * being showed at a drive which doesnt have linux in it ? since my linux is installed in 17 gb partition in 80 gb hard disk,, does it has something to do with it ?

It looks to me you are not following the info twright is giving you. You stick to your auto super grub disk. Don't use that.
Use the live cd from Ubuntu, the one you also used to install the OS.
In the first menu you see (the one with the nice background) choose try Ubuntu from the live CD.
Then, once booted, open a terminal and type the codes twright has given you.
Then choose restart, take out the cd when asked, and boot normally.

---

### Post by DeViLDuD3 on 2009-06-18
ok I did as u said
 
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
grub> 
 
 
still there is no change in the boot menu ?

---

### Post by DeViLDuD3 on 2009-06-19
so ?

---

### Post by twright on 2009-06-19
In this case I do not know what is going on, the commands suggest they have been successful. Unless you want to take this opportunity to do a fresh install and upgrade to ubuntu 9.04, this tutorial from super grub disk might help: [http://www.supergrubdisk.org/w/index.php5?title=Image:English_menu.png](http://www.supergrubdisk.org/w/index.php5?title=Image:English_menu.png)

---

### Post by DeViLDuD3 on 2009-06-20
ok Ireinstalled Ubuntu now I encounter another problem.. Ubuntu freezes when it loads after boot.. :s the bar halts to proceed when it loads...
is there any solution :S ?

---

### Post by twright on 2009-06-22
> **DeViLDuD3 said:**
> ok Ireinstalled Ubuntu now I encounter another problem.. Ubuntu freezes when it loads after boot.. :s the bar halts to proceed when it loads...
is there any solution :S ?
to find more info can you press e (i think) over the ubuntu item on the boot menu then remove the words splash and quiet, this should display an error message if it goes wrong. Can you post that message (or take a picture :)) and someone might be able to give some more info.

---

### Post by DeViLDuD3 on 2009-06-25
ok when I press e at the linux generic it shows me this
GRUB4DOS 0.4.3 2007-12-25, Memory: 639K/1014M, CodeEnd: 0x40D50

root ()/Ubuntu/disks
kernel /boot/Vmlinuz-2.6.27-7-generic root=UUID=5E7F-OBC3 Loop=/Ubuntu/di
initrd /boot/intird.img-2.6.27-7-generic

---

### Post by DeViLDuD3 on 2009-06-26
so got a clue ?

---

### Post by DeViLDuD3 on 2009-06-28
hulo?

---

### Post by AndyCee on 2009-06-28
> **DeViLDuD3 said:**
> ok when I press e at the linux generic it shows me this
GRUB4DOS 0.4.3 2007-12-25, Memory: 639K/1014M, CodeEnd: 0x40D50

root ()/Ubuntu/disks
kernel /boot/Vmlinuz-2.6.27-7-generic root=UUID=5E7F-OBC3 Loop=/Ubuntu/di
initrd /boot/intird.img-2.6.27-7-generic

Get to this point again, select the second line and type 'e' again. The end of the line has been cut off - there should be something like:

kernel /boot... root=... ro quiet splash

Delete "quiet" and "splash" and type 'b' for boot. These are instructions for grub, not supergrub, but they might apply. You won't make any permanent changes.

---

