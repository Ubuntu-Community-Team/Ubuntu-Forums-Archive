---
title: "Lost my splash screen - how can I restore it?"
date: 2009-02-02
forum: Desktop Environments
---

### Post by redandwhitestripes on 2009-02-02
Hi everyone, I'm running Intrepid Ibex and I used to have a splash screen that now gives a console readout when booting or closing. This is not actually making a problem but I'd like to know how to get my screen back. I have not changed any of my appearance options except the theme, which I restored later. 

I also created some partitions - could this have affected my splash screen?

Any advice most welcome.
Greg

---

### Post by caljohnsmith on 2009-02-02
> **redandwhitestripes said:**
> 
I also created some partitions - could this have affected my splash screen?

Yes, changing partitions could have an effect on your splash screen if you did anything that would have changed the UUID of your swap partition. How about posting the output of:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume

```
That way we can check if your swap UUID might be the issue.

---

### Post by redandwhitestripes on 2009-02-02
Thank you. I will do that today and paste the readout here.

---

### Post by eddyjackson on 2009-02-03
I'm curious of the solution to this as well. I'm almost certain I lost my splash screen about the time I changed some partitions and I know for a fact my swap partition UUID changed.

---

### Post by redandwhitestripes on 2009-02-04
Ok here is my readout:

[CENTER][I]greg@greg-laptop:~$ sudo fdisk -lu
[sudo] password for greg: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x075b075b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   142721459    71360698+  83  Linux
/dev/sda2       306568395   312576704     3004155    5  Extended
/dev/sda3       142721460   306568394    81923467+  83  Linux
/dev/sda5       308608650   312576704     1984027+  82  Linux swap / Solaris
/dev/sda6       306568521   308608649     1020064+  83  Linux

Partition table entries are not in disk order
greg@greg-laptop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="c5e646ba-e876-4b24-9de6-66c1516063bd" TYPE="ext3" 
/dev/sda3: UUID="0ed88fbe-153e-4fe2-86db-2e991b937f50" TYPE="xfs" 
/dev/sda5: UUID="df9e9a93-5f97-44a1-b6f4-bb6054414cd9" TYPE="swap" 
/dev/sda6: UUID="d35e52a7-c292-4d38-87a8-eda751b24ea5" TYPE="reiserfs" 
greg@greg-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c5e646ba-e876-4b24-9de6-66c1516063bd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=873bc6a7-9c6d-4ba4-a24d-3b17d4381ad7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
greg@greg-laptop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=873bc6a7-9c6d-4ba4-a24d-3b17d4381ad7
greg@greg-laptop:~$ 
[/I][/CENTER]

---

### Post by caljohnsmith on 2009-02-04
> **redandwhitestripes said:**
> Ok here is my readout:
```

greg@greg-laptop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="c5e646ba-e876-4b24-9de6-66c1516063bd" TYPE="ext3" 
/dev/sda3: UUID="0ed88fbe-153e-4fe2-86db-2e991b937f50" TYPE="xfs" 
/dev/sda5: UUID="[COLOR="Red"]df9e9a93-5f97-44a1-b6f4-bb6054414cd9[/COLOR]" TYPE="swap" 
/dev/sda6: UUID="d35e52a7-c292-4d38-87a8-eda751b24ea5" TYPE="reiserfs" 
greg@greg-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c5e646ba-e876-4b24-9de6-66c1516063bd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=[COLOR="Red"]873bc6a7-9c6d-4ba4-a24d-3b17d4381ad7[/COLOR] none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
greg@greg-laptop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=[COLOR="Red"]873bc6a7-9c6d-4ba4-a24d-3b17d4381ad7[/COLOR]
greg@greg-laptop:~$ 
```

As you can see highlighted in red above, the UUID of your swap partition did indeed change. Both your fstab and resume file use "873bc6a7-9c6d-4ba4-a24d-3b17d4381ad7" while blkid reports the new UUID as "df9e9a93-5f97-44a1-b6f4-bb6054414cd9". To correct the problem, usually the easiest thing to do is to simply change the swap partition UUID back to what it originally was, so how about doing:
```
sudo swapoff -a && sudo mkswap -U 873bc6a7-9c6d-4ba4-a24d-3b17d4381ad7 /dev/sda5
```
Then reboot, see if you have your splash screen, and also do:
```
sudo blkid -c /dev/null
free
```
The blkid command should show the original swap UUID, and the free command should show you have swap space. If not, please post their output. Otherwise let me know how it goes.

---

### Post by redandwhitestripes on 2009-02-05
Many thanks for your help. It is most appreciated and I will let you know how it goes.

---

### Post by Shazaam on 2009-02-07
caljohnsmith...
Your fix for redandwhitestripes fixed a "similar" problem with my setup. But (don't you hate that? :) ), I have developed a unique situation. I have a multi-boot setup...
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    5  Extended
/dev/sda5             126     4369679     2184777   82  Linux swap / Solaris
/dev/sda6         4369743    53817749    24724003+  83  Linux
/dev/sda7        53817813   136086614    41134401   83  Linux
/dev/sda8       136086678   261088379    62500851   83  Linux
/dev/sda9       261088443   469322909   104117233+  83  Linux

```
in which sda8 is Ubu 8.04 and sda9 is Ubu 8.10 and I have a shared swap. Hardy had the no usplash problem and Ibex usplash worked fine. Did your UUID change on swap and Hardy's usplash now works. Unfortunately the Ibex usplash has now quit working. :) I have gone back and switched it in Intrepid so usplash worked but you could probably figure out what happened to Hardy's usplash again.
I think I have a few choices...
1. Choose one or the other to have a working usplash.
2. Add another swap partition and point either Hardy or Intrepid to it.
3. Wait until Jaunty is golden, wipe the 8.04 and 8.10 partitions and install it.
4. Grab a big hammer and trash the pc. NOT an option.
I have tried using the Hardy, Intrepid AND gparted livecds to wipe and replace the original swap partition but the results are the same.

---

### Post by caljohnsmith on 2009-02-07
Shazaam, that makes sense that swap works in one Ubuntu but not the other at this point, because to get swap to work in both Ubuntu's, each Ubuntu must use the same UUID for swap. How about trying this: boot into whichever Ubuntu currently does not have a working swap, and do:
```
sudo blkid -c /dev/null
```
Find the UUID of the swap partition, and then open your fstab:
```
gksudo gedit /etc/fstab
```
And change the UUID of the swap in the fstab to what you get above. Next do the same for your resume file:
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```
And once you've changed the resume file to use the new swap UUID from above, run:
```
sudo update-initramfs -u -k all
```
Reboot, and I think you should be all set. Let me know if you run into problems though.

---

### Post by Shazaam on 2009-02-07
caljohnsmith...
Very handy little line of code there...
```
sudo update-initramfs -u -k all
```
solved my problem at least. I can put my hammer away now. :)
Thank you for your help.

---

### Post by duds2008 on 2009-02-07
Did you modify your menu.lst file and accidentally delete the word splash from your boot parameters?

---

