---
title: "Alcohol 120%"
date: 2009-06-08
forum: General Help
---

### Post by chebbie on 2009-06-08
hey guys..
i have been looking for similar posts but my questions have never been asked actually.

what to do to burn .iso / .cue.bin files on a CD/DVD

how to do a virtual drive? something that could easily be done through the GUI interface in Alcohol120%.

Please, I'm only 2days old on Ubuntu 9.04.

---

### Post by CatKiller on 2009-06-08
> **chebbie said:**
> what to do to burn .iso / .cue.bin files on a CD/DVD

Right-click on the file and select burn to disk.

> how to do a virtual drive? something that could easily be done through the GUI interface in Alcohol120%.

Linux doesn't have drives. If you want to use the contents of a disk image, you'd mount it like any other filesystem. I believe there are some nautilus scripts in the repositories to let you do it through the file manager, but the command to do it in a terminal would be something like ```
sudo mount -t iso9660 -o loop /path/to/iso /path/to/mountpoint
``` where /path/to/mountpoint would be the directory where you want the contents to appear. You might use something like ```
sudo mkdir /media/iso
``` to create this directory, and then the mountpoint would be /media/iso.

---

### Post by meho_r on 2009-06-08
For starters, for burning, try with K3B or Brasero.

For mounting, try [AcetoneISO]("http://www.acetoneteam.org/") or [FuriusISOmount]("http://www.marcus-furius.com/?page_id=14")

---

### Post by Heeter on 2009-06-08
AcetoneIso and right click on burning images.

That is what I use as well,

Heeter

---

### Post by chebbie on 2009-06-09
thanks but regarding the virtual drives.  so, as far as I am understanding it's very important to create a folder beforehand where it's going to be installed.  but if I want to create it on another partition other than the / where i guess it'll install.
what to do then?
in windows we have the option that the virtual drive stays even when you switch off your computer so that next time you can use the virtual drive again and again (used for .iso), how to do it then for the virtual drive to stay?

---

### Post by Wiebelhaus on 2009-06-09
> **meho_r said:**
> For starters, for burning, try with K3B or Brasero.

For mounting, try [AcetoneISO]("http://www.acetoneteam.org/") or [FuriusISOmount]("http://www.marcus-furius.com/?page_id=14")

Fantastic suggestions!

---

### Post by ChaiTan on 2009-06-09
> **chebbie said:**
> thanks but regarding the virtual drives.  so, as far as I am understanding it's very important to create a folder beforehand where it's going to be installed.  but if I want to create it on another partition other than the / where i guess it'll install.
what to do then?
in windows we have the option that the virtual drive stays even when you switch off your computer so that next time you can use the virtual drive again and again (used for .iso), how to do it then for the virtual drive to stay?

If you want the iso to be mounted during boot, you'll have to edit /etc/fstab

Press Alt-F2 and type
```
gksudo gedit /etc/fstab
```
At the end of the file in a new line type
```
/path/to/filename.iso /media/isomountpoint auto loop 0 0
```

replace /media/isomountpoint with the directory where you want to mount the iso.

---

### Post by nandemonai on 2009-06-09
In Jaunty you can just double click .iso files and they'll auto mount.

---

### Post by CatKiller on 2009-06-09
> **chebbie said:**
>  but if I want to create it on another partition other than the / where i guess it'll install.
what to do then?

As ChaiTan says, if you want it to be automatically mounted when the computer boots, you can put an entry in fstab.

Partitions are irrelevant when mounting an iso. It's effectively the same as its own partition; it's another filesystem that you're adding to the rest of them. For convenience sake you might want it to be mounted alongside another partition - if you had a separate data partition, say, mounted at /mnt/data for example, you might find it convenient to mount your iso to /mnt/data/iso so that the files are accessible in the same way that you might already access those data files, but the files that are included in the iso won't take up any more space in the filesystem than the iso file itself does, wherever it is that you've saved it. Say you had a data partition, and that you'd saved your iso file somewhere on there, mounting your iso to /media/iso wouldn't suddenly take up more space on your / partition.

You can mount any number of filesystems this way; they might be physical partitions on the local machine (like a separate /home partition) or a disk image as you're doing, or another filesystem on a completely different machine mounted over the network. It's all the same process in that you take that other filesystem and graft it into the file tree at the mount point. You don't magically take up more hard drive space when you put a cd in the computer even though the contents of that cd have been mounted at /media/cdrom.

---

