---
title: "Computer wont give permission to open files on DVD"
date: 2008-12-31
forum: General Help
---

### Post by Blender Can Do Anything on 2008-12-31
This is my first post on ubuntu forms. I have always been able to solve all my problems by reading posts here, but I couldn't find this one.

I am the new owner of a Bamboo Fun graphics tablet. I went through a bunch of stuff to get the drivers working and going through the tutorials.

The graphics tablet came with a bonus DVD with Adobe Photoshop Elements, Corel Painter Essentials and Color Efex Pro.

When I went to the DVD, every part of the DVD had an X in the top right of their icon. When I try to run parts of the DVD, it says "Permission Denied". Even the icon and .pdf files said "Permission Denied."

I have Ubuntu 8.10 on a Intel Core 2 duo. I have a dual boot with XP. All the files installed fine on Windows.

---

### Post by damis648 on 2008-12-31
Try opening a terminal and entering:
```
sudo chmod 777 /media/cdrom
```
(change cdrom if it's called something)
and then see if it works.

---

### Post by Blender Can Do Anything on 2008-12-31
Thanks for the reply but sadly, no change.
The terminal gave me:

chmod: changing permissions of `/media/cdrom0': Read-only file system


but the files on the DVD remained "Permission Denied".

What exactly does that code do (mean)? I see that it alters the read-only part of the file, but how does "777" relate to read-only?

---

### Post by gilgongo on 2008-12-31
777 basically means "make it totally read/write" - open all permissions utterly.

---

### Post by damis648 on 2008-12-31
> **gilgongo said:**
> 777 basically means "make it totally read/write" - open all permissions utterly.

Yes, and apparently it won't let you change the permissions because it is on a read-only CD. Looks like you will have to do it in root nautilus.
```
gksudo nautilus
```
and then browse to the CD.

---

### Post by lensman3 on 2008-12-31
Not to disappoint you, but you can't write to a CD or DVD for that matter unless the CD/DVD is read-write.  The media by definition is read-only.

However, that said, you should be able to read the the files on the disk if the file type is a known file type.  Take a look at the file "/etc/mtab" and find the CD/DVD mounted there.  This file is updated every time a new disk,DVD,CD,flash, etc is added to your system.  See if the CD/DVD has a field that user=???? or nosuid.  You might have to mount the disk yourself using the mount command and specifying the user name it should be mounted under as well as the files user-group-world mount permissions.  

I have seen similar trouble if the mount point doesn't have the appropriate permissions to read the folder.  If the CD/DVD is mounted as root it is possible that your user doesn't have the stoke to do anything with the file.

Hope this might help you.

---

### Post by Blender Can Do Anything on 2008-12-31
It worked. Thank you.

It does seem a bit extreme though. I remember a long time ago being shown gksudo nautilus by a friend and being told "don't use it unless you have a really really good reason." I suppose this was a good reason.

Any idea as to why the files on a DVD would be denied permission to run? I have used other DVDs on this computer without problems.

---

