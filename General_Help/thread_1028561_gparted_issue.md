---
title: "gparted issue"
date: 2009-01-02
forum: General Help
---

### Post by DMinard on 2009-01-02
I was hoping to resize an NTFS windows XP partition with gparted and it wont let me. if i open gparted and click show features in the gparted menu it tells me that resizing for NTFS is not available. i know that people have used gparted to resize NTFS but y cant i? i am running ubuntu 8.10

[IMG]http://i237.photobucket.com/albums/ff16/dterror/GParted-Features.jpg[/IMG]




OK so evidently i managed to put this in the wrong forum. sry to bother the apple ppl.

---

### Post by 67GTA on 2009-01-02
Is it mounted? You can't resize a mounted volume.

---

### Post by dnairb on 2009-01-02
I believe gparted requires ntfsprogs to work with ntfs partitions.
Install ntfsprogs from synaptic.

---

### Post by mkvnmtr on 2009-01-02
Where is the GParted you are using? Is it on a live disk or one you have installed on your Ubuntu 8.10? If it is on your system you will indeed need to download the program to work with that type partition and unmount the partition. The option to unmount should be found in GParted. If you are using a live Disk I don't know if they have the program to handle that partition but I can't imagine the would have a live disk without it.

---

### Post by pxwpxw on 2009-01-02
The xubuntu 810 Desktop CD gparted has all features enabled for NTFS.

---

