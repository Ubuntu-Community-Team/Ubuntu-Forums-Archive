---
title: "How to automount my XP partitions? (Intrepid)"
date: 2009-02-04
forum: General Help
---

### Post by cd-r80 on 2009-02-04
I have to Intrepid installed. On both machines I cannot see ntfs partitions or yes but only on external disk? How to start to use my win disks? ntfs-3g? says already installed.

---

### Post by taurus on 2009-02-04
Install ntfs-config and use it to configure your ntfs partition(s).

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by cd-r80 on 2009-02-04
I cannot apply when the button is grey?

---

### Post by taurus on 2009-02-04
Is that ntfs partition mounted?  If it is, try to unmount it first before you run ntfs-config.

Otherwise, post the outputs of these commands from a terminal then.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by cd-r80 on 2009-02-04
/dev/sda1   *           1         765     6144831    7  HPFS/NTFS
/dev/sda2             766        9729    72003330    5  Extended
/dev/sda5             766        1402     5116671    7  HPFS/NTFS
/dev/sda6            1403        2932    12289693+   7  HPFS/NTFS
 
fstab is empty ( no sda1...).
 
Are not mounted.

I had today Feisty on same machine with ntfs in use. Just don't remember any more how I did it (few years ago).

blkid

/dev/sda1: UUID="1.........." TYPE="ntfs" 
/dev/sda5: UUID="3B....." TYPE="ntfs" 
/dev/sda6: UUID="9A......" TYPE="ntfs"

---

### Post by taurus on 2009-02-04
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these lines to the end of it.

```
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0   0
/dev/sda5   /media/sda5   ntfs-3g   defaults,locale=en_US.utf8   0   0
/dev/sda6   /media/sda6   ntfs-3g   defaults,locale=en_US.utf8   0   0

```
Save it and exit gedit editing window.  Now, create the new mount points and mount them.

```
sudo mkdir /media/sda1 /media/sda5 /media/sda6
sudo mount -a
df -h
```

---

### Post by cd-r80 on 2009-02-04
Ok now I remember something. It was also perhaps a problem with that locale=en_US.utf8.  I have Xp installed with other language. I should have backed up /etc but I did not do that?  Or What do you think? I use scandinavian keyboard.

---

### Post by taurus on 2009-02-04
Then delete the **,locale=en_US.utf8** from those three new entries in /etc/fstab.

---

### Post by cd-r80 on 2009-02-04
It seems ok now!

---

