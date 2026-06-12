---
title: "LIVEOS: ubuntu can't access my harddrive!"
date: 2009-03-07
forum: General Help
---

### Post by Countra on 2009-03-07
It lists "250GB drive" but when I click on it I get two error messages:
> UNABLE TO MOUNT 250,0 GB MEDIA - DBus error org.freedesktop*etc* did not recieve a reply, etc
and here's number two:
> $logfile indicates unclean shutdown(0,0) Failed to mount '/dev/sda1: Operation not supported because NTFS is marked to be in use. choose one action: *stuff that I can't do because I'm not root*

Also, a bonus question:
Whenever I click the "take screenshot" button, I get over 9000 pop-up's. Wtf, ubuntu? O.o That's a crazy bug...
I'm running the newest ubuntu live cd, 32-bit, yadda yadda. Help, please?

---

### Post by miegiel on 2009-03-07
> **Countra said:**
> It lists "250GB drive" but when I click on it I get two error messages:

and here's number two:


Also, a bonus question:
Whenever I click the "take screenshot" button, I get over 9000 pop-up's. Wtf, ubuntu? O.o That's a crazy bug...
I'm running the newest ubuntu live cd, 32-bit, yadda yadda. Help, please?

Try checking the disk/partition with gparted or in M$ windows. Maybe it wasn't properly dismounted in windows the last time.

---

### Post by taurus on 2009-03-07
Did windows crash on you?

1.  Install ntfsprogs and use ntfsfix to fix that.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
df -h
```

2.  Or use the force option to mount it.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
df -h
```

If you want to take a screenshot, try Applications -> Accessories -> Take Screenshot.

---

