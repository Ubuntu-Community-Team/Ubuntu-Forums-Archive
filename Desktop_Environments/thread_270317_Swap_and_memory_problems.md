---
title: "Swap and memory problems"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Requiem on 2006-10-03
Hello, I have some problems with my memory management.

Lookig at the system monitor it seems like RAM is always ( and I mean ALWAYS) at 100% and then SWAP is always 0%, this despite the fact that i have twice as much swap as RAM as someone adviced me. 

The computer runs agonizingly ssssssssssslow, often with no other cure than hard rebooting...

I notice this happens at it worse when i run the update manager, it never cases to freeze or almos freeze the system (I have left it running for over 8 hours an nothing) And no, it's not slow network, it actualy freezes during the "configuring packages" phase.

As a side result, I'm afraid that something might have break, i mean, hard rebooting in the middle of system reconfiguration has to be bad, although after the reboot everything works normal (still slow, but way more normal)

Any ideas?

---

### Post by anaconda on 2006-10-03
How much memory do you have?
How much swap?

Maybe your swap isn't in use and you haven't got enough RAM..

can you post the output of the following command:
free

---

### Post by amo-ej1 on 2006-10-03
Some general guidelines for looking at memory under linux. The linux kernel tries to use 'as much of your memory as possible'. So when you see that you have free memory (as in ram) it actually means you have too much memory ;). If you have a gigabyte of ram why wouldn't you use it as a disk cache if it can improve the speed ? 
After that, when there's no other way and the system has used all the ram, the swap memory will be used. swapping is slower than using ram memory. But as suggested you should look at the output of free -m 

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        842        168          0         58        480
-/+ buffers/cache:        302        708
Swap:          956        106        850

```

If the swap counter are all zero it means your swap space isn't mounted.
I would guess you issues are related to something else, perhaps a faulty harddisk or some other hardware related issue. Aren't there any error messages in the dmesg output ?

---

### Post by Requiem on 2006-10-03
Firstly, i want to say thank you for putting up with that awful grammar of mine, I can't belive how many typos I tucked in there.

Ok here is my free -m:


```

             total       used       free     shared    buffers     cached
Mem:           218        215          2          0          1         65
-/+ buffers/cache:        149         69
Swap:            0          0          0

```

And just in case, here is fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>           <options>             <dump>  <pass>
proc            /proc           proc         defaults                     0       0
/dev/hda1       /               ext3         defaults,errors=remount-ro   0       1
/dev/hdb1       /media/hdb1     ext3         defaults                     0       2
/dev/hda3       none            swap         sw                           0       0
/dev/hdd        /media/cdrom0   udf,iso9660  user,noauto                  0       0
/dev/hdc        /media/cdrom1   udf,iso9660  user,noauto                  0       0
/dev/fd0        /media/floppy0  auto         rw,user,noauto               0       0


```

---

### Post by nikhilk on 2006-10-04
Try the following to enable your swap.
From a terminal

```
sudo mkswap /dev/hda3
sudo swapon /dev/hda3
```

---

### Post by Requiem on 2006-10-05
both commands return No such file, after looking into /dev I'm surprised to see there is NO hda3.

This shouldn't be a surprise since I used the dapper live cd with Gparted to : 

delete hda2(fat32) and the swap (hda5 i think), resize hda1 to use the old windows partition then use the last 518MB for swap again.

But, when i see the disk usage using the disk mannager (in System|Administration|Disks) it shows that I still have a hda3! It even recognized hda2 as of swap type!

Wich one should I belive? /dev or Disk Manager

---

### Post by anaconda on 2006-10-05
Here is one solution:
[http://www.ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file+anaconda](http://www.ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file+anaconda)

See my post, where I tell How to create a swap-file instead of a swap-partition. And the instruction does work. Don't know why he had problems with the dd -command (it is just basic copying command)

I would believe your disk manager. So you propably have swap in /dev/hda2 and not /dev/hda3. ANd because your fstab-file tries to enable swap from hda3 (which doesn't exist) it fails.

You can also try this command
swapon /dev/hda2
(I wouldn't try mkswap /dev/hda2 , because if it isn't a swap partition all data in it would be destroyed.. And it propably is  swap already anyway..)

if it works you should change the line from your /etc/fstab -file to use swap from hda2
eg.
/dev/hda2  none   swap ...

EDIT: forgot to mention that you dont have ANY swap according to your free -command. So that is indeed your problem..

---

### Post by Requiem on 2006-10-05
Thankyou editing fstab kinda fixed my swap, although only 16% is used the machine feels really faster, maybe latter when i hook it into the net for the updates i'll see, thankyou so much

---

