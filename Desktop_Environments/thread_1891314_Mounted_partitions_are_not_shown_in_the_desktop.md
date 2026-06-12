---
title: "Mounted partitions are not shown in the desktop"
date: 2011-12-05
forum: Desktop Environments
---

### Post by sonnet on 2011-12-05
I installed Xubuntu 11.10 on my desktop.
On live mode it showed my partitions on the desktop as icons.
But once installed  the mounted partitions are not shown into the desktop,
also they are not shown on the left side of Thunar.
I tried to find some setting to change it but I couldn't find anything regarding it in Thunar options.

---

### Post by nshiell on 2011-12-05
How did u mount the partitions?

---

### Post by LewisTM on 2011-12-05
The Xfce desktop or places menu will only list what they recognize as "removable media" i.e. external drives. Those would be user mountable and found by default in /media

From the perspective of the LiveCD, hard disk partitions are external because the OS is run from CD or USB.

For a hard disk-based OS, partitions are internal, they are mounted as / and /home and whatnot. You can control that by editing (with care) the /etc/fstab file. Stuff like CD media, flashdrives and USB HDD will be shown on the desktop. Also, partitions NOT present in /etc/fstab will show up on the desktop for manual mounting.

---

### Post by sonnet on 2011-12-05
> **nshiell said:**
> How did u mount the partitions?

I mounted them during installations all as /media/...

LewisTM : thanks for your explanation

---

### Post by nshiell on 2011-12-05
What is the output of the
```
df
```
command?

---

### Post by sonnet on 2011-12-06
This is the output of the command DF

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            133632328   5446584 121397600   5% /
udev                   4080288         4   4080284   1% /dev
tmpfs                  1635280       988   1634292   1% /run
none                      5120         0      5120   0% /run/lock
none                   4088200        88   4088112   1% /run/shm
/dev/sda3            1356416624 240558196 1114491244  18% /media/Media
/dev/sdb1            346428076    672336 328158144   1% /home
/dev/sdb2            351522036  33758424 314247948  10% /media/VM01
/dev/sdb3            387848572 106724532 279922880  28% /media/Documents
/dev/sdb4            822999684 101459356 720690724  13% /media/Data
/dev/sdc1            267974708   8580228 256714396   4% /media/VM02
/dev/sdc2            911045748    204740 901727728   1% /media/Workspace
/dev/sdc4            774143996 108821604 665322392  15% /media/Winstorage

---

### Post by LewisTM on 2011-12-06
The fact that the partitions are mounted in /media doesn't mean that they will show on the desktop.
If these partitions are found in fstab entries, they will be considered internal by Thunar.

For the sake of the argument, would you mind providing the contents of your /etc/fstab and /etc/mtab files?

To see all available mountable partitions on a side pane, you may try PCManFM file manager. Gigolo may also be helpful.

---

### Post by sonnet on 2011-12-08
> **LewisTM said:**
> The fact that the partitions are mounted in /media doesn't mean that they will show on the desktop.
If these partitions are found in fstab entries, they will be considered internal by Thunar.

For the sake of the argument, would you mind providing the contents of your /etc/fstab and /etc/mtab files?

To see all available mountable partitions on a side pane, you may try PCManFM file manager. Gigolo may also be helpful.

Yeah they are seen as internal (I thought it was an issue or something that could be solved because I was used to nautilus and because on live mode they appeared on the desktop, but your explanation cleared any doubt), and I have no problems of any kind. Just it is (imo) convenient to see them on the desktop and particularly on the side panel when you navigate.
Along with the tab features is the only thing which i think thunar needs.
I considered pcfmman as alternative, but i think I'll live with Thunar as right now my desktop is extremely stable and I don't want mess around (I also doubt pcfmman is as much stable as thunar, although this might be a false myth).
I know it sounds lame, but i don't wanna risk to waste too much time behind it

---

