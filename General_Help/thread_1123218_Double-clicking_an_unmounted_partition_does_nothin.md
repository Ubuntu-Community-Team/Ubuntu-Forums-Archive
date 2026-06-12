---
title: "Double-clicking an unmounted partition does nothing"
date: 2009-04-11
forum: General Help
---

### Post by Endolith on 2009-04-11
I have a USB drive with two partitions on it.  They both show up in Computer with greyed-out unmounted icons, but when I double click them nothing at all happens.  I know I can mount them with the command line but why doesn't the GUI work?  It doesn't produce any errors in the System Log, either.

pmount doesn't work, either:

```
Error: device /dev/sdb2 is not removable

```

It is certainly removable.

---

### Post by jo4hnc on 2009-04-12
Have you tried right clicking on the icon and choosing "Mount Volume"?

---

### Post by Endolith on 2009-04-12
> **jo4hnc said:**
> Have you tried right clicking on the icon and choosing "Mount Volume"?

Yes.  That also does nothing.

"sudo mount" works fine, of course.

---

### Post by Endolith on 2009-04-12
Hmm... I restarted HAL (**sudo /etc/init.d/hal restart**) and now the partitions mount when I double-click them, but I get an error dialog:

> Unable to mount location
Internal error: No mount object for mounted volume




---

### Post by jo4hnc on 2009-04-12
What is the drive's file format? If it's NTFS you might be able to use the ntfs-config tool.

---

### Post by Endolith on 2009-04-12
There are EXT3, NTFS, and FAT partitions, so I don't think it has anything to do with that.

---

### Post by jo4hnc on 2009-04-12
Is there anything in this help posting that might help?

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by Endolith on 2009-04-12
No.  That describes the way it *should* work, but it doesn't work that way.

---

### Post by egalvan on 2009-04-12
> **Endolith said:**
> There are **EXT3, NTFS, and FAT** partitions, so I don't think it has anything to do with that.

Your original post stated that you had two partitions...

Now you give three different file systems...

Hardy did not come with good support for NTFS...
When I first installed Hardy 8.04, I had NTFS problems...
I installed ntfs-config tools and all my NTFS problems went away.

ErnestG

---

### Post by Endolith on 2009-04-12
> **egalvan said:**
> Your original post stated that you had two partitions...

Those were ext3 and fat.  Then I connected two other external USB drives with NTFS and FAT partitions, and they behaved the same way.  I have NTFS-3G turned on, and I can mount them with no problems on the command line, so I'm sure it has nothing to do with the filesystem.

---

