---
title: "Accessing my floppy drive"
date: 2005-06-06
forum: Desktop Environments
---

### Post by Ray Fried on 2005-06-06
Can anyone suggest what I should read in order to learn how to make the floppy disk drive on my notebook accessable from Warty?

Thanks,

Ray

---

### Post by word_virus on 2005-06-06
[QUOTE=Ray Fried]Can anyone suggest what I should read in order to learn how to make the floppy disk drive on my notebook accessable from Warty?

Thanks,

Ray[/QUOTE]
 Here's how I got my floppy drive working in Ubuntu, maybe it'll work for you.
try typing: sudo modprobe floppy 
in a terminal window
Put a floppy disk in the drive
then try mounting the drive by typing: sudo mount /media/floppy
If that works add the line:
floppy
to your etc/modules file

---

### Post by Ray Fried on 2005-06-08
Thanks for your help!

Your suggestion almost solved the entire problem – except for some additional issues. 1) Automating the process and 2) permissions

As for 1) Automating the process, if I do exactly as you say, I can see and copy from the floppy however after adding the line “floppy” to my “etc/modules” file, I thought that I would not have to mount the floppy each time I boot up. What can I do to eliminate the need to mount the floppy each time?

My /etc/fstab has a line in it as follows:
 /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Now for my 2) question, how do I change the permissions so that I can write to the floppy? If I look at the properties for the drive, it says the File Owner is root. Since I am not the owner, I cannot change the permissions.

Thanks,

Ray

---

### Post by word_virus on 2005-06-09
[QUOTE=Ray Fried]Thanks for your help!

Your suggestion almost solved the entire problem – except for some additional issues. 1) Automating the process and 2) permissions

As for 1) Automating the process, if I do exactly as you say, I can see and copy from the floppy however after adding the line “floppy” to my “etc/modules” file, I thought that I would not have to mount the floppy each time I boot up. What can I do to eliminate the need to mount the floppy each time?
[/QUOTE]

To the best of my knowledge, floppy disks can't be auto-mounted cause there's no automatic polling of the drive (like when you plug in a USB flash drive), so you have to tell the operating system every time you put a new disk in.

> 
My /etc/fstab has a line in it as follows:
 /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Now for my 2) question, how do I change the permissions so that I can write to the floppy? If I look at the properties for the drive, it says the File Owner is root. Since I am not the owner, I cannot change the permissions.


I think root owns every file system that's not your "home" directory and maybe "/tmp".  That's why you have to "sudo" to make a new directory under /usr/local, for instance.  You MAY be able to change the floppy drive's mount point by editing the "/media/floppy0" part of your fstab and changing it to mount /dev/fd0 under your home directory ("/home/username/media/floppy0" for example) so you can read/write to the disk w/o using "sudo".  Give it a shot, the worst that'll happen is you won't be able to mount the floppy drive until you change it back (make a copy of the file first!).

Actually, now that I think about it (not at my usual computer, so I'm not sure), there may be a floppy drive group you can add your user name to under Administration -> Users and Groups in the Gnome menu that would probably eliminate the need to edit the fstab, but like I say I'm not at my Ubuntu box now, so I dunno.

Hope this helps!

---

### Post by Ray Fried on 2005-06-11
Thank you very much - you have been a big help. 

Ray

---

