---
title: "Access XP My Documents"
date: 2006-07-22
forum: Desktop Environments
---

### Post by FooAtari on 2006-07-22
Hi folks,

Have a dual boot system.  Ubuntu and XP are installed on the same hard drive.  I have second hard drive formatted in FAT32 that I am using as a shared drive between XP, Ubuntu and a Laptop.

With Ubuntu I have full access to everything on the FAT32 parition expcet My Documents, which has been renamed to Documents.  I can read all files but cannot delete files or write to that folder...

I want to be able to edit and save Documents from Windows (at the moment my Girlfriend uses Windows) and when using Ubuntu (me).

What is Windows doing that is preventing full access in Linux.  I have setup permission for Read, Write and Full Access but still nothing.

I'm guessing it must be to do with it being a system folder or something along those lines, there must be a way to give full access, perhaps need to edit something in the Registry?

Apart from this everything is working how I want it so far.  Help!

---

### Post by Steveire on 2006-07-22
This is because of shakey NTFS support under Linux. I tried the same thing a while ago. It's possible to get write access for NTFS, but you should read into it first and know the risks of data loss. I haven't done it, so I can't really give more advice than that.

---

### Post by its_me_gb on 2006-07-22
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g")

Try this, i also have a shared drive for my xp and ubuntu and this allows me to view and edit/delete files on the drive.

---

### Post by FooAtari on 2006-07-22
The shared drive is formatted in FAT32 not NTFS and that's where the Documents folder is.

---

### Post by FooAtari on 2006-07-22
No way around this then? :(

---

### Post by BigDave708 on 2006-07-22
Ubuntu should be able to access the My Documents folder if it is on a FAT32 partition. It may well be a problem with Ubuntu because I don't think that XP could stop you accessing files when it isn't even booted. The best way to get around the problem would be to create another partition on your hard drive using either Partition Magic in XP or gParted in Ubuntu and make sure you format it as a FAT32 drive.

---

### Post by simonsonjh on 2006-07-22
My folder for My Documents is also locked for writing in Ubuntu.  The permissions are set to prevent write access.  

How can I set the permission to write access?  The permissions dialog is disabled.

---

### Post by simonsonjh on 2006-07-22
I was able to make myself the owner of the fat32 partition containing the windows "My Documents" folder by changing the mounting in etc/fstab to contain "uid=1000,gid=1000".  Then I was able to enable write permission on the properties dialog.

/dev/hda5 	/media/my 	vfat 	umask=0000,uid=1000,gid=1000	 0	 0

---

### Post by FooAtari on 2006-07-23
> **simonsonjh said:**
> I was able to make myself the owner of the fat32 partition containing the windows "My Documents" folder by changing the mounting in etc/fstab to contain "uid=1000,gid=1000".  Then I was able to enable write permission on the properties dialog.

/dev/hda5 	/media/my 	vfat 	umask=0000,uid=1000,gid=1000	 0	 0

I can't get this to work.  Did you change the whole line, as in copy and paste that in? As I dont have uid=1000 so just stuck it in at the end, and there is some information that isnt above.

At the moment mine looks like this

/dev/hdb5       /media/hdb5     vfat    defaults,utf8,umask=0000,uid=1000,gid=1000 0       0

---

