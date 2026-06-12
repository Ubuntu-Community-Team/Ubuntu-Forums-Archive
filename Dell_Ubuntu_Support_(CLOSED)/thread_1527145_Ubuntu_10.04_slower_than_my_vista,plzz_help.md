---
title: "Ubuntu 10.04 slower than my vista,plzz help"
date: 2010-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nsiva007 on 2010-07-08
I'm using the Lucid 10.04 version of ubuntu on my Dell inspiron 1420 notebook with Intel core2 duo @ 1.5 GHZ and have 2GB RAM,i feel that ubuntu is quite slow in performance than my vista,I'm dual booting with vista,start up and shut down are no problem.

The real sluggishness is when i actually work on the system here are the problems,

->Applications are slow to start,like calculator,firefox almost every application
->even opening folder takes 3-4 secs,say it takes time even to  open computer and my drives which are fast in vista
->it takes 4-5 sec to open pdf and other files,and even if i had previously opened one and again opening the same it takes same time to do it....

Is it possible to make my system faster?

Btw I'm using Compiz fusion,but it made no difference to performance coz even before installing it my performance was same as this......

---

### Post by jarviser on 2010-07-09
Strange, should beat Vista hands-down - my 1520 of almost identical spec is very fast, less than 0.5 sec to open any folder including browsing NTFS windows files, less than 1 sec to open a .pdf. I would not try to tweak it - should not need it. Check the install partitions.

How big is Swap and what partition sizes and formats did you use?

Check available memory, and how full the other partitions are with terminal commands 

free

and

df -T

and come back

---

### Post by nsiva007 on 2010-07-09
Well juzz now checked all swap and memory and here I've attached the screenshot of the information....
I'm juzz stunned by your computers performance,coz my ubuntu didn't perform like that i can't figure out what the problem is...!!
My hard drive has 2 partitions one is shown as 32GB and other 71GB file system....
plzz help me out with this : -)

---

### Post by jarviser on 2010-07-09
The root (/) looks OK but you don't seem to have a /home partition. Use the System/Administration/Disk-Utility to check if you have a swap (Double click on the hard disk icon)

Of the 3 physical partitions on my disk, one is a small system reserved boot partition, one is Windoze,  and the third one is split into 3 logical partitions, one for /home (ext3), one for / (ext4) and one for Linux swap (a few GBytes)

You might want to download "GParted" to CD, and boot the PC with it to repartition the disk that way for a fresh install, or else to delete any Linux partitions and reinstall Ubuntu to use "all unallocated space". It should work out how big to make /, /home and swap.

[IMG]http://www.jarviser.co.uk/jarviser/images4/linuxdiskformat.png[/IMG]

---

### Post by mörgæs on 2010-07-10
This machine should be fast with Ubuntu. 

Does the command **top** indicate a heavy load on the processor? Press q for quitting top.

---

### Post by nsiva007 on 2010-07-10
Thanks, for your replies, i had a problem with grub today coz i formatted the MEDIADIRECT drive yesterday so i backed up all data and reinstalled only ubuntu on my 120 GB with 4.9 GB swap and 4.9 GB extended and 115 GB is file system....!!!
now system is working fine and normal....!!!

---

### Post by mörgæs on 2010-07-10
Good! If more people would reinstall the system, when something went wrong, we could save a lot of questions here.

---

### Post by nsiva007 on 2010-07-11
Lol... yea i had no other way out coz my grub was affected,it asked me to give grub rescue,i had no idea how to rescue grub :-) i thought full install was the only way to get my computer working....!!!
hey i install on entire disk,now my file system is 115 GB,i store all my data here only,will there be any problems coz of this??

---

### Post by Pizack on 2010-07-11
As long as you don't fill up the drive completely you should be fine.  I'm assuming you have a swap still, as just about the only way to avoid having one is to prevent it on purpose (I think).

---

### Post by jarviser on 2010-07-11
> **nsiva007 said:**
> Lol... 
hey i install on entire disk,now my file system is 115 GB,i store all my data here only,will there be any problems coz of this??

Not a problem in use - Having /home as part of the / partition is not a problem, but like in Windows where by default the data is in "My Documents" in the C: drive rather than in an additional D: drive, it makes it more difficult to reinstall the OS as you have to move the data to a spare drive first.  Specifying /home on a separate partition on the disk allows you to reinstall without the format option on /home and would leave the data intact on a reinstall. If  like me you have 50GB of media files it takes a couple of hours to shift it onto a USB drive!

---

### Post by nsiva007 on 2010-07-11
>  Specifying /home on a separate partition on the disk allows you to  reinstall without the format option on /home and would leave the data  intact on a reinstall

Since I've installed on entire disk,is there a way to do what yo said,i.e,specify a partition for my /home folder,can i create a new partition now?? my file system now is 115 GB, storing all my files in /home only...

---

### Post by jarviser on 2010-07-11
As I said in my first reply, I would have created the partitions using GParted (Downloaded to CD) then used the manual partition option in the install screen.

There's probably a way to do it afterwards but someone else will need to explain how.

---

