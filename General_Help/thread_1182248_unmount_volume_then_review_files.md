---
title: "unmount volume then review files"
date: 2009-06-08
forum: General Help
---

### Post by sailthesea on 2009-06-08
Hi there I was wondering if anyone can tell me an easy way to do this in Nautilus?
 I got a whole pile of CDs out the car and want to  label them and store them properly so I get a pen and start popping them into my laptop then realised to take it and write on it I have to unmount it and can't just copy down the info Doh!
 How can I review the disc files after it out of the drive?
 Thanks

---

### Post by justleen on 2009-06-09
make a quick dump of the contents?
```
 ls /media/cdrom > /home/user/contents 
```
the output file you can open with any text editor, thus you have a file list of de CDROM which is not in the drive any more.
If you need all the files on the disk, use find instead of ls

---

### Post by sailthesea on 2009-06-11
Sweet! Thanks!:D

---

### Post by synapsys on 2009-06-11
Just so you know you can use standard output ">" to dump the contents of any command used in the terminal to a text file. Just be sure to give it a destination.

---

