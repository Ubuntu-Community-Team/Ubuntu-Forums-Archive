---
title: "Getting storage drive to show in Places"
date: 2023-03-12
forum: Desktop Environments
---

### Post by peyre on 2023-03-12
I have an SSD for the system and a big HDD for bulk storage.  I have it mounted automatically on bootup and everything is working fine.  However, before I reinstalled Xubuntu I had it showing in Places, so it was very easy to open - but now it doesn't.  It's easy enough to open something else and click on Storage on the left in Thunar, but it would be nice to skip that step, and go directly to it from Places.

My HDD mounts in /media/Storage.  Here are the active lines in /etc/fstab.

```
UUID=8784334d-51f5-4d7e-8c64-c2b42719abe4 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=3D1B-BAAB  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=2c2262cb-3edb-4003-ba6a-4ed7aa4c03e7 /media/Storage ext4 defaults 0 2
/dev/fd0 /media/floppy0 auto rw,user,sync,noauto,exec,utf8 0 0
```

---

### Post by ActionParsnip on 2023-03-14
If you navigate to /media in your file manager you can then drag the "Storage" folder to places to add the bookmark

---

### Post by peyre on 2023-03-14
That'd be awesomely easy!  Where do I drag it exactly?  Dragging it onto the Places icon on the panel doesn't do anything, and there is no Places directory under ~/.

---

### Post by ActionParsnip on 2023-03-14
I'd have said places but you tried it. Is there a bookmark menu option on the file manager to add it that way?

---

### Post by ajgreeny on 2023-03-15
The simplest way is probably to add the volume to your own bookmarks in the left hand panel by dragging and dropping it into the bookarks panel and then move it up as near the top of the list as you want by dragging it up the list.

You need to have thunar set to show bookmarks in the panel, not folders, of course, for this to work.

---

### Post by ActionParsnip on 2023-03-15
What file manager are you using here, please?

---

### Post by peyre on 2023-03-15
> **ActionParsnip said:**
> What file manager are you using here, please?

Again, this is Thunar, the default for Xfce.

---

### Post by peyre on 2023-03-15
> **ajgreeny said:**
> The simplest way is probably to add the volume to your own bookmarks in the left hand panel by dragging and dropping it into the bookarks panel and then move it up as near the top of the list as you want by dragging it up the list.

You need to have thunar set to show bookmarks in the panel, not folders, of course, for this to work.

Thanks, but I don't see where to set Thunar to show bookmarks rather than folders--either under View or Preferences.  Selecting Bookmarks -> Add Bookmark doesn't seem to do anything either.

---

### Post by #&amp;thj^% on 2023-03-15
<snip> I read the first post
Try:
```
sudo mount -a
```

---

### Post by ajgreeny on 2023-03-15
You can show Bookmarks in the left hand pane by hitting Ctrl+B as shown in the **View - Sidebar** menu, then Ctrl+E if you want to go back to folders or tree view.

So use Ctrl+B to see all places or bookmarks, view up your mounted data drive at /media and drag the storage folder that will show there into your Bookmarks, placing it where you want in the list.

---

### Post by peyre on 2023-03-15
Hey, that worked thanks!

---

