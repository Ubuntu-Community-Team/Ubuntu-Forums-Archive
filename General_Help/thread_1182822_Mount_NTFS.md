---
title: "Mount NTFS"
date: 2009-06-09
forum: General Help
---

### Post by zimbot on 2009-06-09
Friends,

I have upgraded from 7.04 to ubuntu 8.04 and since then i have been unable to mount NTFS volumes.

I can no longer mount the 2nd drive on my machine ( local , this is a dual boot xp & ubuntu machine )

Nor can i access any of the shared dir on the lan.
I used to use a tool NTFS configuration tool - that worked great - but no longer does ( can that still be a solution? )

also i find this bit of wisdom

mount -t cifs //host_ip_address/share_name -o username=win_user_name,password=password_for_user /mount/point


Ok -- i could try that - a couple of Qs
1. Do i need to make a mount point
like mkdir under /mnt     or something like that?

would a good practice be to make a dir ( as a mount point )
that i would consistantly use for my 2nd dirve 
( local sata , NTFS named Data2  - win data drive )

a ls /dev :: shows a sda , sda1 , sda2 sda3 sda5 ( no 4 ) sdb sdb1 

and a second mount point that i could use as a wildcard to diffrent win shares on my lan?

of course _ i long for the days 
when I would go to Places , network , windows network, workgroup , the machine


thanks

---

### Post by merlinus on 2009-06-09
```

sudo apt-get install ntfs-config

```

Look for it in the menus afterwards.

---

### Post by zimbot on 2009-06-09
i seem to already have that - i had it before

 sudo apt-get install ntfs-config
[sudo] password for j
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.

maybe the confg went goofy on the upgrade

---

### Post by merlinus on 2009-06-09
Did you tick the boxes in the gui to enable mounting and writing of ntfs devices?

```

sudo ntfs-config

```

---

### Post by colau on 2009-06-27
> **zimbot said:**
> i seem to already have that - i had it before

 sudo apt-get install ntfs-config
[sudo] password for j
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.

maybe the confg went goofy on the upgrade
To mount ntfs drive
```

sudo apt-get install ntfs-3g
sudo mkdir /media/MYDRIVE
sudo ntfs-3g /dev/sdaX /media/MYDRIVE
cd /media/MYDRIVE
ls

```
sudo ntfs-3g /dev/sdaX /media/MYDRIVE
Here X is the value of the partition.

---

### Post by merlinus on 2009-06-28
I may be mistaken, but shouldn't the command be:

sudo mount -t ntfs-3g /dev/sdaX /media/MYDRIVE

---

### Post by colau on 2009-06-28
> **merlinus said:**
> I may be mistaken, but shouldn't the command be:

sudo mount -t ntfs-3g /dev/sdaX /media/MYDRIVE
Probably it's
```

mount -t ntfs /dev/sdaX /media/MYDRIVE

```

---

### Post by colau on 2009-06-28
> **merlinus said:**
> I may be mistaken, but shouldn't the command be:
sudo mount -t ntfs-3g /dev/sdaX /media/MYDRIVE
To have full read wrire permission:
```

sudo ntfs-3g /dev/sdaX /media/MYDRIVE

```
I use this with the live cd "systemrescuecd".

---

