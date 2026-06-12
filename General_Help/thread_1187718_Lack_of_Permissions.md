---
title: "Lack of Permissions"
date: 2009-06-14
forum: General Help
---

### Post by solidname on 2009-06-14
Hello all,
 My macbook just freaked out, and I can't boot into Mac OS at the moment. A friend of mine recommended booting off of an Ubuntu disk to access and recover the files. While I *can* see the files on my harddrive, I can't copy the files onto an external harddrive, as I'm told I don't have the proper permissions.

  Would anyone know how to get around this, and if it's not possible, if there's any other software that would allow me to recover my files? Thanks.

---

### Post by loomsen on 2009-06-15
Use the livecd and openup a terminal, to log in as root, do:

```
sudo su -
```

Now you got supercow powers 8)

---

### Post by aysiu on 2009-06-15
If the drive is FAT32, NTFS, or Ext3, you can just use Alt-F2 ```
gksudo nautilus
``` If the external drive is HFS+, though, I don't think you can write to it.

---

### Post by asmoore82 on 2009-06-15
```
gksudo nautilus
```
[SIZE="5"]**+1**[/SIZE]

but remember that just that one Nautilus "File Browser" window will have root privilege -
closing it will abort the data transfer.

---

