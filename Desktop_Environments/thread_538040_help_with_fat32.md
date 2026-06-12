---
title: "help with fat32"
date: 2007-08-29
forum: Desktop Environments
---

### Post by tropcky on 2007-08-29
look is the past i had a proplim with ntfs partitions  and i fixed it by ur help 4 sure 
but when i reinstall ubuntu  i made it fat32 from the partitioner  in the set up 
and of corse i made an ext3 for the system 
any way  after i done  i cant see the fat32 partion  i dont know y 
so plez help cuz i am out of free space and the fat32 have 60 g free space  so i need it 
thank u

---

### Post by Jagged on 2007-08-29
if you are trying to see the fat 32 partition with windows (which, why else would you need it?) windows doesn't like fat32 partitions made in linux for some reason. get a hold of a windows 98 boot disk and load iit up then type fdisk at the command prompt. then when you are in fdisk look at the partitions and it should see that partitiion. delete it and then make a new one. after that reboot into the disk again and type format C:\ at the command prompt....that should get you going...and here's a link at which you can download a floppy image for the windows 98 boot disk [bootdisk.com]("http://files.frashii.com/~bootdisk/newjersey/boot98se.exe"):popcorn:
oh and C for the format may not neccisarily be what drive letter you want but it is most likely

DOS was wonderful

---

### Post by tropcky on 2007-08-29
will i dont wanna see it by widows  i wanna see in in linux  i am using ubuntu and its the only system in my ps  so i wanna see it from here

---

### Post by tropcky on 2007-08-29
look iam thinkin about backup my data and go to some frend and format all my hard desk all over agen 
so i have 2 hard desks  i will made in the frest 1 ext3 partion and swep partion   4 the system 
so that will give us anther 2 free partions 
so what u think  i gonna made them 
ntfs ? fat16 ? fat 32 ?   i need them 4 my data 
so tell me wiche one will be full access read and write without any proplim 
thank u

---

### Post by trak87 on 2007-08-29
Here's the basic process. Identify where the fat32 partition is with fdisk. Look for the dev (device) info:

```
sudo fdisk -l
```

Let's say it turns out to be /dev/sda6. Then create a mount point for it:

```
sudo mkdir /media/myfat32drive
```

Then make an entry in /etc/fstab (File System TABle) containing those two pieces of info (the device and the mount point):

```
sudo nano /etc/fstab
```

And then add something like the following:

```
/dev/sda6  /media/myfat32drive   vfat    defaults,utf8,umask=000    0   1
```

Save, exit and reboot. You should now be able to access your fat32 drive from the /media/myfat32drive directory.

---

### Post by kellemes on 2007-08-29
For sharing data between tux and Windows you can better use ext3. It has much more features as fat32 and there are fine ext3-drivers available for Windows.

---

### Post by Jagged on 2007-08-29
if you are only using linux why would you want to use fat32 or ntfs?...just use ext3, it sure makes things much easier

---

### Post by tropcky on 2007-08-29
ferst of all thank u trak87  and thank u kelleme
but u telling me to make the data partion  ext3  ?

---

### Post by tropcky on 2007-08-29
oky guys i will make it ext3   i hop[ it works cool with me cuz i am sick of my pc 
imagen  staying 20 days  tray 2 fix only 1 proplim  lol thats feels bad

---

### Post by kellemes on 2007-08-29
> **tropcky said:**
> ferst of all thank u trak87  and thank u kelleme
but u telling me to make the data partion ext3  ?

For sharing between the 2 OS's you can use ext3.
On windows you need some software to access the partition..
some links.
[http://www.ext2fsd.com/]("http://www.ext2fsd.com/")
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by tropcky on 2007-08-29
will thanks god i kicked microshit windows out of my ps after i bean hacked and lose all my data 2 month ago

---

