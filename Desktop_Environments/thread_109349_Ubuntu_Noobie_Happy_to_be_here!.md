---
title: "Ubuntu Noobie Happy to be here!"
date: 2005-12-28
forum: Desktop Environments
---

### Post by noobybuntu on 2005-12-28
Hello, all!

I just installed Ubuntu5.10 and I love it.  After a few minor problems with the partitioning process, I'm up and running.

I have one problem, though.  I can't save anything to my floppy drive.  According to Ubuntu, I don't have permission to write to the floppy.

Can someone tell me how to set the proper permissions for  /media/floppy0?  I've found commands for setting permissions for files and folders, but I haven't yet seen how to do it for a mountable device.  And can it be done from the GUI, or must I do it from a terminal window?

Thanks for your help.

---

### Post by Christophercmolik on 2005-12-28
Try inserting a floppy, and right-click the icon that should pop up on the GNOME desktop.  Select mount, and you should be good to go.  If this does not work, please show us your /etc/fstab file

---

### Post by rjwood on 2005-12-28
see this thread for your floppy problem:
[unable to access to floppy disk - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=85777&highlight=floppy")

and Welcome!!!!!

---

### Post by noobybuntu on 2005-12-28
[QUOTE=Christophercmolik]Try inserting a floppy, and right-click the icon that should pop up on the GNOME desktop.  Select mount, and you should be good to go.  If this does not work, please show us your /etc/fstab file[/QUOTE]

The drive is already mounted; I can read files from it, but I can't save a file to it.

Here's my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>      <dump>  <pass>
proc            /proc           proc    defaults       0       0
/dev/hda5       /               ext2   defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults       0       0
/dev/hda6       none            swap    sw             0       0
/dev/hdc        /media/cdrom0   udf,iso9660user,noauto     0       0
/dev/fd0        /media/floppy0  ext2,vfat   rw,user,noauto  0       0


I recently changed the "type" for "/media/floppy0" from "auto" to "ext2,vfat".

The error message when I attempt to save an Open Office (Excel) spreadsheet file to /media/floppy0 is:

"Error saving the document FILENAME:
/media/floppy-/FILENAME.xls does not exist."

If I attempt to copy the file, using Nautilus, from the hard drive to /media/floppy0, I receive the following  message:

"Error while copying to "/media/floppy0".
You do not have permissions to write to this folder."

So there must be somewhere I can change the permissions controlling the floppy.  I just haven't been able to figure out where.

---

### Post by Lin-X on 2005-12-29
Hi, Nube! Glad to have you here! I am also somewhat new to Ubuntu, but not to Linux. I happen to be having problem similar to yours; if I find something that works for me, I will post here right away. I hope you don't get too discouraged with Ubuntu.
Any troubles you have at first are well worth solving, believe me. By the way, don't pay too much attention to some of the moaning and groaning in these forums from people who wish Ubuntu would do this or that like Red Hat, or Mandrake, or some other Linux. Every Linux is a little different. If you want to OWN your operating system (and therefore, your computer), you have to be willing to take responsibility for it. Once this minor problem is solved, you'll be glad you came to Ubuntu.

---

### Post by Lin-X on 2005-12-29
Found it! Type floppy drive in the Search box; scroll down the resulting list of posts til you see one "Unable to access floppy drive". It was posted by mxyzptlk about a week ago and answered by General Zod. I think this is what we both need.

---

