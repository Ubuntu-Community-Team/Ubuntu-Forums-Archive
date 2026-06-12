---
title: "I'm a Grub 17 victim.. how to fix it?"
date: 2009-04-12
forum: General Help
---

### Post by geova87 on 2009-04-12
Ok guys.. here's the deal... First of all I don't have my Ubuntu installer disk so I'm downloading it again...

My problem started when I tried to install UbuntuStudio in a new partition, I installed it and ran it but then I deleted that partition and since I deleted it I keep getting the damn grub 17 error... I accessed a shell mounted on hda1 (which as my ubuntu info) using the restore broken system in the UbuntuStudio disc and when I typed sfdisk -lU I got that my syst. is suppossed to boot from hda1 which should be working since its the one described with Linux.

I can cd my files and everythings there but how can I get the syst to boot right?  This is driving me nuts, I've spent the whole night looking for an answer because didn't want to bother u guys but I had no other options...

thanx in advance for the help...

---

### Post by hyper_ch on 2009-04-12
best is to download supergrub, burn it and run it and restore grub from there.

---

### Post by geova87 on 2009-04-13
Okay, I got the Super Grub... Now where should I go? thnx in advance...

---

### Post by Aubergines on 2009-04-13
A few more details would be handy for example:

a) How is your system set up? Dual boot? and what os in what partition.

b) You deleted Ubuntustudio by wiping the partition, you now get a grub error 17 which is a failure to mount the Ubuntustudio partition. But now you're trying to repair Ubuntustudio using a default Ubuntu as a base? So if it works it'll convert your Ubuntu into Ubuntustudio? This is the part I'm a bit confused on. If you remove the partition I can't see the repair disk restoring it and the data.

---

### Post by meierfra. on 2009-04-13
> Okay, I got the Super Grub... Now where should I go? thnx in advance...

Choose

#  GRUB => MBR & !LINUX! (1) AUTO ; - ))) 


at the first screen.

If that does work, check out this [link]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub")

---

### Post by geova87 on 2009-04-13
> **Aubergines said:**
> A few more details would be handy for example:

a) How is your system set up? Dual boot? and what os in what partition.

b) You deleted Ubuntustudio by wiping the partition, you now get a grub error 17 which is a failure to mount the Ubuntustudio partition. But now you're trying to repair Ubuntustudio using a default Ubuntu as a base? So if it works it'll convert your Ubuntu into Ubuntustudio? This is the part I'm a bit confused on. If you remove the partition I can't see the repair disk restoring it and the data.


I had Ubuntu 8.10 full, no dual boots. And I had no partitions made to my disk since I didn't needed it.  I created a partition for Ubuntu Studio so I was running two main partitions one with Ubuntu OS 8.10 and one with Ubuntu Studio, I had some problems with Ubuntu Studio so I deleted the info in that partition and left it blank (just to store documents, pics and sstuff).  Up to that point everything was going fine 'till I restarted. When I restarted I got the Grub error. I don't want to repair UbuntuStudio I want my desktop back(Ubuntu 8.10) I can access it through a terminal window and everythings there, stored, but i cannot load the system as a normal desktop. I'm getting that grub 17 error. I'm going to try now the SUPERGRUB thing to see if it works.

Thanks for the help.

---

### Post by geova87 on 2009-04-13
Ok, I'm not sure how the hell it happened but it fixed with the SuperGrub disk.  Now the only thing I want to fix is that in the booting screen I get the Ubuntu logo and the line running across the screen, then instead of filling it goes black and begins to name everythings that's loading... I liked it when the bar just filled up. How do i put it back that way?

OMG thanx to all you guys who helped! you are the best!

---

### Post by meierfra. on 2009-04-13
> it goes black and begins to name everythings that's loading..
Sound like a problem with your swap partition. Post the output of

```
cat /etc/fstab
sudo bklid -c /dev/zero
free
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by brunogirin on 2009-04-13
> **geova87 said:**
> Now the only thing I want to fix is that in the booting screen I get the Ubuntu logo and the line running across the screen, then instead of filling it goes black and begins to name everythings that's loading... I liked it when the bar just filled up. How do i put it back that way?

Check that the "kernel" line in the /boot/grub/menu.lst file ends with "quiet splash". If you want, you can modify it on the fly when you boot to try out.

---

### Post by geova87 on 2009-04-13
> **brunogirin said:**
> Check that the "kernel" line in the /boot/grub/menu.lst file ends with "quiet splash". If you want, you can modify it on the fly when you boot to try out.

defoption=quietsplash

so I guess that's not the problem..

---

### Post by geova87 on 2009-04-13
> **meierfra. said:**
> Sound like a problem with your swap partition. Post the output of

```
cat /etc/fstab
sudo bklid -c /dev/zero
free
cat /etc/initramfs-tools/conf.d/resume
```


I have a real problem with my partitions because I have a partition made (the one I created to install ubuntu studio) but I can't use it. It says permision denied. Its a 50 gb partition and I want to use it, I don't know what may be causing this problem.

---

### Post by atomizer on 2009-04-13
I think your problem with your partition is, that the UbuntuStudio-user has all the rights for that partition and not the 8.10 user.


You could reformat that partition or use the chown-command (change owner)

If you use the chown- command, the partition has to be mounted.

format:
```
sudo mke2fs -j /dev/partition
```

change owner:
```
sudo chown -R yourname /path/to/partition
```

---

### Post by geova87 on 2009-04-13
> **meierfra. said:**
> Sound like a problem with your swap partition. Post the output of

```
cat /etc/fstab
sudo bklid -c /dev/zero
free
cat /etc/initramfs-tools/conf.d/resume
```

geovannie@geovannie-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fba6d73e-c555-4499-aebe-5d73b49f746d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b457ae1b-77e2-4380-b181-4a89aa31d338 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
geovannie@geovannie-laptop:~$ sudo bklid -c /dev/zero
[sudo] password for geovannie: 
sudo: bklid: command not found
geovannie@geovannie-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        505020     499420       5600          0       1528      80856
-/+ buffers/cache:     417036      87984
Swap:            0          0          0

---

### Post by meierfra. on 2009-04-13
```
sudo: bklid: command not found
```

My bad. It's supposed to be

```
sudo blkid -c /dev/zero

```

---

### Post by meierfra. on 2009-04-13
Also you forgot this command:

```
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by geova87 on 2009-04-13
> **meierfra. said:**
> Also you forgot this command:

```
cat /etc/initramfs-tools/conf.d/resume
```

geovannie@geovannie-laptop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=b457ae1b-77e2-4380-b181-4a89aa31d338


the blkid -c /dev/zero doesnt respond..  just goes down a line outside of all directories... just a blank line...

i think the problem is the sda5.. since i boot from sda1..

---

### Post by meierfra. on 2009-04-13
> blkid -c /dev/zero doesnt respond.

I'm really sorry.   It supposed to be 

```
sudo blkid -c /dev/null
```

---

### Post by geova87 on 2009-04-13
MOre info..

I have two partitions.. sda1 and sda6.. 

from sda1 i boot ubuntu and it has all the info (its 20gb large)

sda6 (which i can now access because i changed the owner) has 50 gbs...

I had no partitions done before... it is since i have partitions that im having all this problems... how can i merge those 50 gbs back to the sda1... like it was before... is it posible? at least with the gparted i can do it.. since it won´t let me resize sda1 partition... i guess it´s because is mounted... any solution for this?

---

### Post by geova87 on 2009-04-13
> **meierfra. said:**
> I'm really sorry.   It supposed to be 

```
sudo blkid -c /dev/null
```

geovannie@geovannie-laptop:~$ sudo blkid -c /dev/null
[sudo] password for geovannie: 
/dev/sda1: UUID="fba6d73e-c555-4499-aebe-5d73b49f746d" TYPE="ext3" 
/dev/sda5: UUID="1003e18b-43b5-4b9f-800b-35440d44a4b3" TYPE="swap" 
/dev/sda6: UUID="87a517ae-6d3b-4cd9-b80d-86e5ff464fae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="b0f9aa9f-4f73-42bd-9c1b-acefa0fefd4d" TYPE="swap" 
/dev/sda8: UUID="9a14d3bf-150b-40e0-8953-ff6079204019" TYPE="swap"

---

### Post by meierfra. on 2009-04-13
Lets fix your swap problem first:


```
sudo mkswap -U b457ae1b-77e2-4380-b181-4a89aa31d338 /dev/sda8
sudo swapon /dev/sda8
```

Check that your swap is working now:

```
free
```

The first number in the last line should  not longer be zero.

---

### Post by geova87 on 2009-04-13
> **meierfra. said:**
> Lets fix your swap problem first:


```
sudo mkswap -U b457ae1b-77e2-4380-b181-4a89aa31d338 /dev/sd8
sudo swapon /dev/sda8
```

Check that your swap is working now:

```
free
```

The first number in the last line should  not longer be zero.

got an err

geovannie@geovannie-laptop:~$ sudo mkswap -U b457aelb-77e2-4380-b181-4a89aa31d338 /dev/sda5
[sudo] password for geovannie: 
mkswap: error: UUID parsing failed

---

### Post by geova87 on 2009-04-13
sorry i wrote sda5 instead of sda8,, still i got an err...

geovannie@geovannie-laptop:~$ sudo mkswap -U b457ae1b-77e2-4380-b181-4a89aa31d338 /dev/sd8
/dev/sd8: No such file or directory
ctory

---

### Post by geova87 on 2009-04-13
my linux swaps (as appear in gparted) are sda8, sda7 and sda5

---

### Post by meierfra. on 2009-04-13
Try it again:

 sudo mkswap -U b457ae1b-77e2-4380-b181-4a89aa31d338 /dev/sda8

It looks like the formating  introduced a space in the UIID (just before the "d338".  Make sure that before you hit "enter" that the uuid (b457ae1b-77e2-4380-b181-4a89aa31d338 ) contains no spaces.

---

### Post by geova87 on 2009-04-13
Ok, I think I got it right now.. chek it out..

geovannie@geovannie-laptop:~$ sudo mkswap -U b457ae1b-77e2-4380-b181-4a89aa31d338 /dev/sda8
[sudo] password for geovannie: 
Setting up swapspace version 1, size = 1373520 KiB
no label, UUID=b457ae1b-77e2-4380-b181-4a89aa31d338
geovannie@geovannie-laptop:~$ sudo swapon /dev/sda8
geovannie@geovannie-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        505020     494076      10944          0       5288      53992
-/+ buffers/cache:     434796      70224
Swap:      1373516          0    1373516
geovannie@geovannie-laptop:~$

---

### Post by meierfra. on 2009-04-13
> Ok, I think I got it right now.
Great, that looks good.

> sda6 (which i can now access because i changed the owner) has 50 gbs...

I had no partitions done before... it is since i have partitions that im having all this problems... how can i merge those 50 gbs back to the sda1... like it was before... is it posible? at least with the gparted i can do it.. since it won´t let me resize sda1 partition... i guess it´s because is mounted... any solution for this?

To merge the partitions you need to use gparted from the LiveCD. You also will have to delete your  50GB partition. So if you have any data on that partition you have to back it up or move it to /dev/sda1.
Of course, as with any partitioning, you should backup all your valuable data.

Boot from the LiveCD, start gparted and RightClick  each of the partition (and if available) choose "Umount" or "Swap Off"

Delete  /dev/sda5,/dev/sda6 and /dev/sda7.

Shrink the extended partition (/dev/sda2?)  as much as possible.

Enlarge  /dev/sda1 as much as possible.

---

### Post by geova87 on 2009-04-13
> **meierfra. said:**
> Great, that looks good.



To merge the partitions you need to use gparted from the LiveCD. You also will have to delete your  50GB partition. So if you have any data on that partition you have to back it up or move it to /dev/sda1.
Of course, as with any partitioning, you should backup all your valuable data.

Boot from the LiveCD, start gparted and RightClick  each of the partition (and if available) choose "Umount" or "Swap Off"

Delete  /dev/sda5,/dev/sda6 and /dev/sda7.

Shrink the extended partition (/dev/sda2?)  as much as possible.

Enlarge  /dev/sda1 as much as possible.

OK I´ll try this tomorrow because i left my disc at work and the servers are pretty slow so it´s going to take some time to download...

If I restart the system will I still have all the data loading or it´s supposed to be gone?

---

### Post by geova87 on 2009-04-13
by data loading I mean that when I turn on my pc after I get the screen with the ubuntu logo and the little line going from side to side, instead of the bar filling up it takes me to a black screen which says something like loading files needed to boot     [ok] 
and then appear a whole bunch of stuff loading (i guess system drivers and stuff)

I want to have the bar filling up like before.. not all that info that comes up on the screen.

---

### Post by meierfra. on 2009-04-13
> I want to have the bar filling up like before.. not all that info that comes up on the screen.

Fixing your swap partition, should have fixed this problem as well.

---

### Post by geova87 on 2009-04-13
yes! its all fixed.. thnx a lot.. i´ll do the partition stuff tomorrow and post the results.. thanx for everything!!

---

### Post by geova87 on 2009-04-14
Hey, I did all you told me to but it won't let me resize the sda1...

---

### Post by geova87 on 2009-04-14
It's working now. Im waiting for it to be done so I can restart and Check that everythings in order

---

### Post by geova87 on 2009-04-14
Ok I fixed the partitions but I have again the boot screen going, guess I'll have to fix partitions again... should I do the same commands I did yesterday and post you the output here?

---

### Post by geova87 on 2009-04-14
geovannie@geovannie-laptop:~$ sudo blkid -c /dev/null
[sudo] password for geovannie: 
/dev/sda1: UUID="fba6d73e-c555-4499-aebe-5d73b49f746d" TYPE="ext3" 
geovannie@geovannie-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        505020     498292       6728          0      11704     109156
-/+ buffers/cache:     377432     127588
Swap:            0          0

Again I want to get rid of the boot screen which names everything that's loading, instead I want the Ubuntu bar filling Up

---

### Post by meierfra. on 2009-04-14
Did you delete all the swap partitions? Post the output of 

```
sudo fdisk -lu
```

If you still  have a swap partition, just do

```
sudo mkswap -U b457ae1b-77e2-4380-b181-4a89aa31d338 /dev/sda5
```

I'm assuming  that the swap partition is /dev/sda5, if not replace /dev/sda5 by the device name of the swap partition

---

### Post by geova87 on 2009-04-14
geovannie@geovannie-laptop:~$ sudo fdisk -lu
[sudo] password for geovannie: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9c2d9c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   155380679    77690308+  83  Linux
/dev/sda2       155380680   156296384      457852+   5  Extended
/dev/sda5       155380743   156296384      457821   83  Linux


no swap partitions...

---

### Post by meierfra. on 2009-04-14
it seems something went go wrong with your partitioning.

Anyway, you can still use

sudo mkswap -U b457ae1b-77e2-4380-b181-4a89aa31d338 /dev/sda5


to turn /dev/sda5 into a swap partition.

But /dev/sda5 only has about 220MB, which is a little small for a swap partition. So I recommend to boot from the LiveCD again and use gparted to shrink /dev/sda1 by about 1GB (make sure to shrink /dev/sda1 from the right end point, don't move the left end point) and then increase the extended partition /dev/sda2  and /dev/sda5 by the same amount.

Then use

sudo mkswap -U b457ae1b-77e2-4380-b181-4a89aa31d338 /dev/sda5

in a terminal, to make sure that the swap  partition has the correct UUID.

---

### Post by tamas305 on 2009-04-14
I had the same error and I managed to fix with Super Grub Disk, its a linux based quasi-OS that is oriented towards system rescue. It has a GUI and you can just follow the on-screen instructions than reinstall grub with all of its files in the correct place.

Perhaps these instructions I found on another forum may help

"(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell."

Good luck,
-tamas

---

### Post by meierfra. on 2009-04-14
tamas305:  You should always read all the post in a  thread before posting. Grub Error 17 was fixed a long time ago. See post 7.

---

### Post by geova87 on 2009-04-16
thnx for eveyrthin.. i finally had time today to do the swap thing and it worked like a charm... you rule son!

---

### Post by meierfra. on 2009-04-16
> it worked like a charm...
Great. Did you resize the swap partition?  If not, I suggest  to monitor your swap use from while to while. Just type

```
free
```

and see how much  of your swap  you are using. If  you  use most of your swap, you should really enlarge your swap partition. Otherwise you risk a freeze up.

---

