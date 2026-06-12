---
title: "Cannot Copy File or Folder error"
date: 2009-03-04
forum: General Help
---

### Post by SonOfOdin on 2009-03-04
Heya

I have an external hard drive that I use with two computers - one with Hardy and one with MS XP Home.

I havent had any dramas moving files to the hard drive, but I have just noticed that files/folders that were created when the HDD was attached to the linux box can not be copied to the XP machine.

Any clues how to fix this dilemma?  The problem has become compounded because while I use linux more often the XP box needs more of the files on that HDD.  And, I went and sorted out the directory in linux, creating some order to the mess...  now I cant move the files across :(  Its almost like the file system on the hdd has partially been changed - its an NTFS partition.

Pretty please.
Cheers

EDIT: Oh, the error message that I get is 
Error Copying File or Folder
Cannot copy file: Cannot read from the source file or disk.

---

### Post by SonOfOdin on 2009-03-04
Oh crap.  The XP machine has just been freshly installed.  Could it be an account permission thing?

---

### Post by taurus on 2009-03-04
Did you remember to unmount the external drive before you unplugged it in Ubuntu?

---

### Post by SonOfOdin on 2009-03-04
Um, thats a good question taurus.  Cheers for the reply firstly.  Im pretty sure that I didnt unmount...  :(

I need to use the hdd on the XP machine and wont have access to the Linux box for a couple of days.  Is there a work around?  If I run the Ubuntu installation CD Live, will unmounting the drive there fix the problem?

Cheers

---

### Post by taurus on 2009-03-04
If you copy files from Ubuntu to your external harddrive, then decide to just unplugged it from the machine without unmounting it first, then files will be either corrupted or not written over completely.  

I think that is why you can't access those files now since they are all corrupted.

---

### Post by SonOfOdin on 2009-03-04
Thing is I can still open the files, I can still move the files around the external hdd within the XP OS.  I just cant copy them from that drive to the internal HDD within XP.

I have to say that the files are not corrupted.

---

