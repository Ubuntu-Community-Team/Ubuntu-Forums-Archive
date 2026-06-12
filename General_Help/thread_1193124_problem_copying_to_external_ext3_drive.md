---
title: "problem copying to external ext3 drive"
date: 2009-06-21
forum: General Help
---

### Post by HKAlly on 2009-06-21
Hi I've formatted an external hard drive as ext3 using GParted but when I copy files and folders to it using 'cp -r' I am advised that I have no permissions to access them, although I can delete them using 'rm -r'. I can also not 'copy & paste' to the ext3 drive. The permissions listed in the file browser are 'drwx'. I have backed up to this drive using 'rdiff-backup' and all is well I have full permissions to all the files. I have had no problem copying to a FAT32 formatted external drive

I'm new to Ubuntu and Linux and hope someone can help

---

### Post by credobyte on 2009-06-21
What if you use sudo ?
```
sudo cp -r something to_somewhere
```

---

### Post by HKAlly on 2009-06-21
Hi Thanks for replying. That is what I tried, it copies over but when I then try to open  the folders or files in the File Browser I have no permissions. I've now found that I can open files (gnome-open) and list files (ls) etc from the Terminal if I use sudo but not from the File Browser. When I try to change properties in the File Browser it says I have no permission.

---

### Post by callan79 on 2009-06-21
> **HKAlly said:**
> Hi I've formatted an external hard drive as ext3 using GParted but when I copy files and folders to it using 'cp -r' I am advised that I have no permissions to access them, although I can delete them using 'rm -r'. I can also not 'copy & paste' to the ext3 drive. The permissions listed in the file browser are 'drwx'.


Hi HKAlly,

It's probably the 'owner' of the drive causing you issues. Can you do this..

```
ls -l /media/
```

Also please tell us which of the entries is the drive you're talking about?

More than likely you need to do this :

```
sudo chown yourusername:yourgroupname /media/name_of_drive
```

If you're not sure, post the output of the first command above and we'll tell you more.

Cheers
Callan

---

### Post by blueridgedog on 2009-06-21
It might help to see the files and permissions.  Can you post the output of 

```
ls -al
```

In the directory with the fies and the directory used as the mount point you are trying to copy to?

---

### Post by HKAlly on 2009-06-21
Hi Guys That was the problem the stuff I copied over was owned by root. chown sorted it Thanks to you all

---

