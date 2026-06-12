---
title: "[SOLVED] cant read my ntfs partion"
date: 2008-03-12
forum: Desktop Environments
---

### Post by tropcky on 2008-03-12
hi 
now Ubuntu cant see one of my partions i dont know y   it all ntfs and its all working but only  one  its not even in my computer to mount it      
any help pleeez ?

---

### Post by tropcky on 2008-03-13
any help ?

---

### Post by {BzF}~JOKesTER on 2008-03-13
Is It An External Hard Drive Or Internal??

And Is It USB ESATA Firewire??

IDE SATA - And Is It Setup Using A RAID Array?

:)

---

### Post by vikrant82 on 2008-03-13
Probably the partition is dirty and needs a chkdsk. 

Either run chkdsk /f in windows or install ntfsprogs from repos and run ```
ntfsfix dev/sdxX 
```

Or try a manual mount, 

```
sudo mount /media/XXX
```  [if it is in fstab]

or ```
sudo mount -t ntfs-3g /dev/sdaX /media/path 
```You will probably see what error occured while mounting.

You can also force mount by ```
sudo mount /media/XXX -o force
```

---

### Post by taurus on 2008-03-13
Boot into windows and shut it down cleanly instead of using the hibernation to shut down your machine.

---

### Post by tropcky on 2008-03-13
> **vikrant82 said:**
> Probably the partition is dirty and needs a chkdsk. 

Either run chkdsk /f in windows or install ntfsprogs from repos and run ```
ntfsfix dev/sdxX 
```

Or try a manual mount, 

```
sudo mount /media/XXX
```  [if it is in fstab]

or ```
sudo mount -t ntfs-3g /dev/sdaX /media/path 
```You will probably see what error occured while mounting.

You can also force mount by ```
sudo mount /media/XXX -o force
```

its still the same :
 when i did ntfsfix dev/sdxX   i got 
:~$ ntfsfix dev/sda2
Failed to determine whether dev/sda2 is mounted : No such file or directory
Mounting volume... Error opening partition device : No such file or directory
Failed to startup volume : No such file or directory
FAILED
Attempting to correct errors... Error opening partition device : No such file or directory
FAILED
Failed to startup volume : No such file or directory
Volume is corrupt. You should run chkdsk.

---

### Post by {BzF}~JOKesTER on 2008-03-13
Do You Have The libntfs-3g12 Package Installed?

Get It By Typing:

apt-get update

And

apt-get install libntfs-3g12


That Might Help - Also Just Try Mounting Through /etc/fstab

gedit /etc/fstab

And Add Your HDD To The List -{It Might Already Be Present - Just Change To "Default" If So}

---

### Post by tropcky on 2008-03-13
i installed libntfs-3g12

and in gedit /etc/fstab
 its already ther   but still not working 

and i dont have windows to clen or to shut it down to fix that

---

### Post by {BzF}~JOKesTER on 2008-03-13
Does It Mount Into The Computer Folder And At Least Show The Icon For The Drive???

If So Do This:

Right Click The Icon - And Select "Properties"

Go To The "Drive" Tab And Click The "Settings" Tab.

Under "Mount Options" Type This:

force

Now Go To The "Volume" Tab And Then "Settings" And In "Mount Options" Type:

force

Now You Should Be Good 2 Go!!!!

Keep Me Updated !

---

### Post by prshah on 2008-03-13
> **tropcky said:**
> its still the same :
 when i did ntfsfix dev/sdxX   i got 
:~$ ntfsfix dev/sda2
Failed to determine whether dev/sda2 is mounted : No such file or directory
Mounting volume... Error opening partition device : No such file or directory
Failed to startup volume : No such file or directory
FAILED
Attempting to correct errors... Error opening partition device : No such file or directory
FAILED
Failed to startup volume : No such file or directory
Volume is corrupt. You should run chkdsk.

Post the output of ```
sudo fdisk -l
```

---

### Post by tropcky on 2008-03-13
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e061e05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2555        5049    20041087+   7  HPFS/NTFS
/dev/sda3            5050        9730    37592064+   f  W95 Ext'd (LBA)
/dev/sda4            2433        2495      506047+  82  Linux swap / Solaris
/dev/sda5            5050        9730    37592064    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x383f383e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10338    78147584    7  HPFS/NTFS
tropcky@tropcky-Linux:~$

---

### Post by tropcky on 2008-03-13
> **{BzF}~JOKesTER said:**
> Does It Mount Into The Computer Folder And At Least Show The Icon For The Drive???

If So Do This:

Right Click The Icon - And Select "Properties"

Go To The "Drive" Tab And Click The "Settings" Tab.

Under "Mount Options" Type This:

force

Now Go To The "Volume" Tab And Then "Settings" And In "Mount Options" Type:

force

Now You Should Be Good 2 Go!!!!

Keep Me Updated !
will its not in the computer folder its only in the media folder and its empty  with 14 g free space  just like home folder   but my real partion is not ther

---

### Post by vikrant82 on 2008-03-14
> when i did ntfsfix dev/sdxX i got
:~$ ntfsfix dev/sda2
Failed to determine whether dev/sda2 is mounted : No such file or directory
Mounting volume... Error opening partition device : No such file or directory
Failed to startup volume : No such file or directory


Sorry buddy, My bad. I missed a leading '/'

```
sudo ntfsfix /dev/sda2
``` 

Also on sudo fdisk -l you should get a list of partitions like this 

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1044     8385898+   7  HPFS/NTFS
/dev/sda2            1045       12160    89289270    f  W95 Ext'd (LBA)
/dev/sda5            1045        3916    23069308+   7  HPFS/NTFS
/dev/sda6            3917        4961     8393931    7  HPFS/NTFS
/dev/sda7            4962        6215    10072723+  83  Linux
/dev/sda8            6216        6266      409626   82  Linux swap / Solaris
/dev/sda9            6267        8877    20972826    7  HPFS/NTFS
/dev/sda10           8878       10444    12586896   83  Linux
/dev/sda11          10445       12160    13783738+  83  Linux
```

Choose whatever drive is not mounting and try running the ntfsfix command appropriately.

---

