---
title: "mount swap ?"
date: 2006-08-13
forum: Desktop Environments
---

### Post by th0mas on 2006-08-13
just a question, why does my swap partition does not appear when i call the 'mount' command ?

```
$ mount
/dev/hda8 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
udev on /dev type tmpfs (rw)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-6-686/volatile type tmpfs (rw)

```

here is my fstab :

```
$ cat /etc/fstab
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none    swap    sw      0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

is it mounted though it's not mentionned as mounted ?
thanks for your answer !

---

### Post by taurus on 2006-08-13
It should show up with

```

free

```

---

### Post by th0mas on 2006-08-13
great i'm rassured !

i also could have noticed it using ```
top
```

---

### Post by zasf on 2006-12-31
> **taurus said:**
> It should show up with

```

free

```

what if it does not?

```
matteo@burnt:~$ free
             total       used       free     shared    buffers     cached
Mem:       1036024     561996     474028          0     157808     207876
-/+ buffers/cache:     196312     839712
[COLOR="Red"]**Swap:            0          0          0**[/COLOR]
matteo@burnt:~$ top

top - 12:40:34 up 22 min,  3 users,  load average: 0.62, 0.20, 0.17
Tasks:  92 total,   2 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.7%us,  2.0%sy,  0.4%ni, 79.5%id, 10.0%wa,  0.4%hi,  0.1%si,  0.0%st
Mem:   1036024k total,   563604k used,   472420k free,   157904k buffers
[COLOR="Red"]**Swap:        0k total,        0k used,        0k free,   208080k cached**[/COLOR]

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                             
 5801 root      15   0 49500  24m  11m S  3.9  2.4   0:17.61 Xorg                                                
    1 root      15   0  1632  544  452 S  0.0  0.1   0:00.54 init                                                
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                         
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 events/0                                            
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                             
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                             
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                           
    9 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                              
  121 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod                                             
  157 root      25   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                    
```

here is fstab and fdisk

```
matteo@burnt:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        6424    36242640    f  W95 Ext'd (LBA)
/dev/sda3            6425       12161    46082452+  83  Linux
/dev/sda5            6375        6424      401625   82  Linux swap / Solaris
/dev/sda6            1913        5098    25591482    7  HPFS/NTFS
/dev/sda7            5099        6373    10241406   83  Linux

Partition table entries are not in disk order
matteo@burnt:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 -- converted during upgrade to edgy
UUID=853a9cf6-d4c2-474f-8384-0b33ae57923d / ext3 defaults,errors=remount-ro 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=df93ad94-ef99-4b4a-96c2-e752d2b42f1d /media/linux2 ext3 defaults 0 2
# /dev/sda6 -- converted during upgrade to edgy
UUID=D48C60BD8C609C2C /media/secondo ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=9EA03185A03164C5 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=aaf79fb7-39a7-4163-9202-24e3dd1782fd swap swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#//192.168.1.2/condi /media/condisuz2 smbfs defaults,username=defaults,password=defaults,gid=46 0 0
#//netbiosname/sharename /media/sharename cifs guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//z2/condi /media/condisuz2 cifs guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

swap doesn't get mounted and I see no error in dmesg.. what should I do? How can I fix it?

Thanks,
Matteo

---

### Post by taurus on 2006-12-31
The entry for swap in your /etc/fstab is wrong.  Open a terminal, Applications -> Accessories -> Terminal, and edit /etc/fstan with

```
gksudo gedit /etc/fstab
```
and replace this line.
```
UUID=aaf79fb7-39a7-4163-9202-24e3dd1782fd swap swap sw 0 0
```
with
```
/dev/sda5   none   swap   sw   0   0
```
Save it and run
```
sudo mount -a
free
```

---

### Post by zasf on 2006-12-31
> **taurus said:**
> The entry for swap in your /etc/fstab is wrong.  Open a terminal, Applications -> Accessories -> Terminal, and edit /etc/fstan with

```
gksudo gedit /etc/fstab
```
and replace this line.
```
UUID=aaf79fb7-39a7-4163-9202-24e3dd1782fd swap swap sw 0 0
```
with
```
/dev/sda5   none   swap   sw   0   0
```
Save it and run
```
sudo mount -a
free
```

thanks!!! now it works.. but who broke it?

---

### Post by taurus on 2006-12-31
> **zasf said:**
> thanks!!! now it works.. but who broke it?

Probably upgrading from Dapper to Edgy did it (but not me)!  I only fixed it...  :mrgreen:

---

### Post by chadk on 2007-01-06
Had this problem as well after upgrade.  I tried replacing the long UID number with the more familiar /dev/hda5 but that didn't work when I tried to mount or swapon -a it.  So I just did this:
```

sudo mkswap /dev/hda5
sudo swapon -a

```

---

### Post by psybonix on 2007-01-23
cheers chadk

that worked a treat ):P

---

### Post by haricharan on 2007-02-13
For me the same problem occured sda6 was my swap partition. I did the following....
```
sudo mkswapon /dev/sda6
```
Output was 
```
Setting up swapspace version 1, size = 1077473 kB
no label, UUID=[COLOR="SeaGreen"]0107518a-2865-4002-b555-08d117634a03[/COLOR]
```
Then do
```
sudo swapon -a
```
Once you do this your swap space is visible through 
```
free
``` or ```
top
```
But when you reboot the swap does not mount again. So you have to copy the generated UUID and paste it in the fstab file
```
sudo /etc/fstab
```

OLD swap line in fstab

```

# /dev/sda6 -- converted during upgrade to edgy
[COLOR="Red"]UUID=eb148e40-0942-4a58-b09a-c0aac255e75e[/COLOR] none swap sw 0 0
```

NEW swap line in fstab
```

# /dev/sda6 -- converted during upgrade to edgy
[COLOR="SeaGreen"]UUID=0107518a-2865-4002-b555-08d117634a03[/COLOR] none swap sw 0 0
```

Now even if you reboot your computer the swap partitions are automatically mounted...

---

### Post by dcstar on 2007-02-13
> **haricharan said:**
> 
.......
But when you reboot the swap does not mount again. So you have to copy the generated UUID and paste it in the fstab file
.......

You don't "have" to use a UUID at all.

UUIDs are great concept for removable drives, or drives that somehow will have their physical designation changed (like when moving a disk from one IDE channel to another, or from a Master to Slave device), but for most people they are not that useful - and has been shown here, they can be bloody inconvenient.

Just using the standard "hard" designation in a fstab file is more than adequate - as long as you realise that changing the physical setup of drive may cause issues in the future.

---

### Post by haricharan on 2007-02-14
thanks for the info David.. :) ....i just tried this and its working for me.....

---

