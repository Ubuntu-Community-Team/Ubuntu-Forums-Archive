---
title: "Mounting a NTFS drive - Not working"
date: 2009-02-21
forum: General Help
---

### Post by Compintuit on 2009-02-21
Hello all. I've ran into some trouble, and have to ask for help again. I recently moved into xubuntu as I found ubuntu too slow for my computer. however, I'm having some trouble. I dual boot, and I can't seem to mount my windows partition anymore. I had previously followed the instructions here, [http://ubuntuforums.org/showthread.php?t=767879](http://ubuntuforums.org/showthread.php?t=767879) but they won't work for me now. I can edit fstab fine, find the right drive fine, but when I go to mount all, I get this message:

[mntent]: warning: no final newline at the end of /etc/fstab
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.


So can someone explain what's going on? Here's my readout of the drives:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03e103e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7298    58621153+   7  HPFS/NTFS
/dev/sda2            7299        9729    19527007+   5  Extended
/dev/sda5            7299        9559    18161451   83  Linux
/dev/sda6            9560        9729     1365493+  82  Linux swap / Solaris

---

### Post by taurus on 2009-02-21
What's the error message if you try to mount it by hand from a terminal?

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
df -h
```

---

### Post by drs305 on 2009-02-21
Do you have only one drive? Fstab is looking for sdb1, whereas it appears that windows is on sda1.

Open fstab for editing.
```

sudo cp /etc/fstab /etc/fstab.old
gksudo gedit /etc/fstab  # or the text editor of your choice

```

Change *sdb1* to ***sda1*** if you only have the one drive, and that the mount point in that line exists (example: /media/windows).
Go to the end of the last line in fstab and hit enter to create a new line at the end.
Save the file.

Mount the windows partition:
```

sudo mount /dev/sda1

```

If you have problems, please post:
```

cat /etc/fstab
df -Th
sudo fdisk -l

```

Edit: composed and posted before seeing Taurus' entry

---

### Post by crazyness003 on 2009-02-21
You can download an app called Disk Manager from the repos. It does [almost] everything you can do with manual setting and modding. You can even do force mounts. 
plus It [almost] eliminates the risk of typos.
(but as we all know, faeces happens)

```
sudo apt-get install disk-manager
```

---

### Post by Compintuit on 2009-02-21
> **taurus said:**
> What's the error message if you try to mount it by hand from a terminal?

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
df -h
```

It mounted fine by hand...

[QUOTE=drs305]Do you have only one drive? Fstab is looking for sdb1, whereas it appears that windows is on sda1.

Open fstab for editing.
Code:

sudo cp /etc/fstab /etc/fstab.old
gksudo gedit /etc/fstab  # or the text editor of your choice

Change sdb1 to sda1 if you only have the one drive, and that the mount point in that line exists (example: /media/windows).
Go to the end of the last line in fstab and hit enter to create a new line at the end.
Save the file.

Mount the windows partition:
Code:

sudo mount /dev/sda1

If you have problems, please post:
Code:

cat /etc/fstab
df -Th
sudo fdisk -l[/QUOTE]

Darn - all I had to do was change the sdb to sba and add another line - that was really easy. I kinda feel like an idiot - I should have seen both of those. Anyway, thanks, the both of you.

crazyness003, I know there are apps for everything, but part of the reason I moved to xubuntu was because I wanted to learn to edit config files. Also, I seems a shame to install an app to do what a single edit to a file can do. But thanks anyway.

---

### Post by crazyness003 on 2009-02-22
> **Compintuit said:**
> It mounted fine by hand...



Darn - all I had to do was change the sdb to sba and add another line - that was really easy. I kinda feel like an idiot - I should have seen both of those. Anyway, thanks, the both of you.

crazyness003, I know there are apps for everything, but part of the reason I moved to xubuntu was because I wanted to learn to edit config files. Also, I seems a shame to install an app to do what a single edit to a file can do. But thanks anyway.
hey, im glad it worked. And I understand. Its just that sometimes the windows side of me gets the best of me :)

have fun hacking

---

