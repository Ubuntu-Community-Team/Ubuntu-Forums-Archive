---
title: "External Hard Drive"
date: 2005-03-31
forum: Desktop Environments
---

### Post by pfe1223 on 2005-03-31
I'm a newbie, and I really need to access some files on my exernal hard drive.  I can mount the drive with no problems, but ubuntu does not recognize the file types nor file folders.  I see the file names with their extention, but under the file type column, it says "unknown".  I don't want to put XP back on my laptop, but I need to access these files.  Any suggestions?

---

### Post by mirtux on 2005-03-31
Hi,
 what about accessing it through the console? And a note, for UNIXes system the extension does not mean anything.... You can control what kind of files are using the **file** command
An example could be
 ```

$ file /etc/fstab 
/etc/fstab: ASCII text

```
Regards,
MC

---

### Post by silicon.pyro on 2005-03-31
[QUOTE=pfe1223]I'm a newbie, and I really need to access some files on my exernal hard drive.  I can mount the drive with no problems, but ubuntu does not recognize the file types nor file folders.  I see the file names with their extention, but under the file type column, it says "unknown".  I don't want to put XP back on my laptop, but I need to access these files.  Any suggestions?[/QUOTE]

What file system are you using on the external drive?

---

### Post by pfe1223 on 2005-03-31
I am using fat32, I think.  When I tried mount -t ntfs... I got an error.  However, when I did mount -t vfat... there were no problems.

---

### Post by silicon.pyro on 2005-03-31
> I am using fat32, I think. When I tried mount -t ntfs... I got an error. However, when I did mount -t vfat... there were no problems.

What kinds of files are trying to open?

It sounds like you can see the files, and have access to them, but gnome doesn't understand what to do when you double-click on one.  As in a previous post, linux doesn't care about the file extensions, but you should be able to match them up yourself and open them with an application that understands the file.

---

### Post by pfe1223 on 2005-03-31
I tried to use Open Office to open an Office 97 Word document.  When I selected the open feature,  it did not recognize any of the files on the mounted drive.  It just said, "............".

---

### Post by mirtux on 2005-04-01
[QUOTE=pfe1223]I tried to use Open Office to open an Office 97 Word document. When I selected the open feature, it did not recognize any of the files on the mounted drive. It just said, &quot;............&quot;.[/QUOTE]
You can try to load the file using OpenOffice and the command line..
**ooffice "filename"**

Regards,
MC

---

### Post by Heliode on 2005-04-01
I think I know whats going on. Would I be right if I assumed you're also seeing folders as 'files' on the fat32 partition? I had exactly the same issue with a fat32 partition. You can fix it by putting the following in your /etc/fstab (you need to be SuperUser):

[device]        [mount point]    vfat    rw,user,auto,umask=000  0 0

The [device] is where the device node goes. probably something like /dev/sda1. Mount point would be something like /media/sda1. You should change 'sda1' to whatever your PC calls your external HD. (this is the name it gives the icon it pops on your desktop when you plug it in). Using our example, this would be the full line you'd have to add;

/dev/sda1        /media/sda1    vfat    rw,user,auto,umask=000  0 0

what really makes this work is the 'umask=000' part. This makes it so that you can access it normally with your file manager.

If you don't always have the device plugged in, you can change 'auto' to 'noauto'. Then, when you want to mount it, you just do 'mount /media/sda1' for example.

Good luck and let us know how it worked out!

---

