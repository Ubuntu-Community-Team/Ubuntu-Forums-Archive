---
title: "AutoMount Nautilus GVFS Problem"
date: 2008-12-29
forum: Desktop Environments
---

### Post by crudolphy on 2008-12-29
I have taken an older computer that was running Windows XP poorly and upgraded it.  Running an AMD64 single core 3000+ processor with 1GB of ram and two 40GB PATA hard drives.

I took the original Windows drive and switched it from the master to the slave and took a different HD and made it the master.  I left the entire Windows installation on the now slave intact.  I installed 8.10 AMDX64 on the now master drive.  Installation was flawless and it recognized the windows install on the slave and asked to import settings and documents etc.  I let it do this and it appears that it imported everything flawlessly.:D  When it booted up into my new Ubuntu install it mounted the slave as "40.0 GB Media".  This showed up in the "Places" menu and then when I accessed the drive by clicking the "40.0 GB Media" in the "Places" menu it put an icon on the desktop by the same name.

After I checked that the import of documents, favorites, desktop wall paper, etc looked complete, I formatted the slave with Gparted for an ext3 file system, I created a directory under home/jennifer/extra and edited the fstab file adding the line:

```
/dev/sdb1 /home/jennifer/extra ext3 relatime,errors=remount-ro 0 1

```
And then rebooted the machine.

Upon reboot it now mounts the slave drive on the mount point defined above as /home/jennifer/extra but it continues to show the "40.0 GB Media" label in the "Places" menu and continues to put the icon on the desktop labeled "40.0 GB Media".

If I right click on the icon and go to properties it says

> Type: folder (inode/directory)
Volume: 40.0 GB Media

I don't want to use the config editor to turn off the feature of putting dynamically mounted drives on the desktop with an icon.  Now that this drive is part of the file system and mounted by fstab I don't want the icon on the desktop, I don't want the label in the "Places" menu unless my user (Jennifer) wants to bookmark it.  Also whether I wanted to keep the desktop icon and the menu choice in "Places" or not it shouldn't be named "40.0 GB Media" :confused:it should be named "extra".

Note that I have checked the /media directory and it is empty.

How can I fix this in my installation?

Thanks for any and all help.

---

### Post by crudolphy on 2009-01-01
Bump - anybody with some help?

---

### Post by ugm6hr on 2009-03-17
> **crudolphy said:**
> Also whether I wanted to keep the desktop icon and the menu choice in "Places" or not it shouldn't be named "40.0 GB Media" :confused:it should be named "extra".

You can fix this by labelling the ext3 drive with e2label:

```
sudo e2label /dev/sdb1 extra
```

I'm not sure whether it is possible to remove non root partitions from Places (I don't think you can).

---

### Post by ScottHW on 2009-03-29
I also have been looking for a method for trying to remove extraneous partitions from my Places menu.

Does anyone know definitively of a method that works, for the TOP HALF of the Places menu (i.e. User Folder, "Desktop", "File System", "37.5 GB Media", "Network Servers", "Trash")?

---

### Post by brallan on 2009-07-24
> **ScottHW said:**
> I also have been looking for a method for trying to remove extraneous partitions from my Places menu.

Does anyone know definitively of a method that works, for the TOP HALF of the Places menu (i.e. User Folder, "Desktop", "File System", "37.5 GB Media", "Network Servers", "Trash")?

The places menu is just a series of nautilus bookmarks. open the filebrowser on any directory (or type nautilus in terminal) and look in Bookmarks>Edit bookmarks> and just delete the ones you don't want.

---

