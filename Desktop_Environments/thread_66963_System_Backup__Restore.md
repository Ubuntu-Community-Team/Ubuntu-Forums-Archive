---
title: "System Backup / Restore"
date: 2005-09-18
forum: Desktop Environments
---

### Post by jhuff on 2005-09-18
What is the best way to backup/restore your system?  I'm manly concerned with all my Kontact data, Firefox links,  and files in my home directory.

---

### Post by matthew on 2005-09-18
If you only have a couple of things to back up the easiest thing to do would be to figure out where those things are stored on the hard drive and just copy those files to a removable medium like a cd-rom or an external usb drive.

For something on the scale you are wanting to do I would recommend this thread which has a great howto on the subject of backup/restore. The method mentioned there has been useful to me and made recovery from a dead hard drive a simple matter for me when I had a major hardware failure.

[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by jhuff on 2005-09-19
Thanks,  I'll take a look at that thread.  Do you have any experience with the usb drives?  Can you boot kubuntu from one of them?

---

### Post by Xian on 2005-09-19
You could easily just tar the directory and burn to CD. 

```
# sudo tar -cvpjf archive.tar.bz2 /path/to/directory
```

---

### Post by Ptero-4 on 2005-09-19
[QUOTE=matthew]If you only have a couple of things to back up the easiest thing to do would be to figure out where those things are stored on the hard drive and just copy those files to a removable medium like a cd-rom or an external usb drive.

For something on the scale you are wanting to do I would recommend this thread which has a great howto on the subject of backup/restore. The method mentioned there has been useful to me and made recovery from a dead hard drive a simple matter for me when I had a major hardware failure.

[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)[/QUOTE]
 Another trick is to set nautilus to show the invisible files and then copy your home folder to your backup media.

---

### Post by matthew on 2005-09-19
[QUOTE=jhuff]Thanks,  I'll take a look at that thread.  Do you have any experience with the usb drives?  Can you boot kubuntu from one of them?[/QUOTE]
I have used both the usb keychain type flash memory as well as the external hard drive with usb interface. Both have worked well for me in Ubuntu and have been detected just by plugging them in. I have never tried to boot from one, though. I think it would depend on whether your motherboard and bios support booting from an external device, so it isn't likely to be something easy to answer without direct access to your machine.

---

### Post by matthew on 2005-09-19
[QUOTE=Xian]You could easily just tar the directory and burn to CD. 

```
# sudo tar -cvpjf archive.tar.bz2 /path/to/directory
```[/QUOTE]
That's basically what the page I referred him to does, just with more explanation and less knowledge of precisely what he wants to back up required. I almost gave the exact same answer as you did, Xian, and then I remembered the other thread and thought it might be a good intro to tar.

---

### Post by matthew on 2005-09-19
[QUOTE=Ptero-4]Another trick is to set nautilus to show the invisible files and then copy your home folder to your backup media.[/QUOTE]
That would work well. I like tar because it also compresses the data and therefore takes up a bit less space. Your idea would work quite well for someone who doesn't like the command line and isn't worried about saving space.

---

### Post by jeremy on 2005-09-21
I use a knoppix cd and partimage to make image files of my HD

---

