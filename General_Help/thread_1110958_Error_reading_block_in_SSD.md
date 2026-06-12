---
title: "Error reading block in SSD"
date: 2009-03-30
forum: General Help
---

### Post by LepeKaname on 2009-03-30
Ubuntu Intrepid(32b) 

Few weeks ago I bought a SSD disk of 32GB to store my important documents (because they are suppose to rarely fail). 

However, this morning I turned my PC on and got the next message in /var/log/fsck/checkfs:

```
fsck 1.41.3 (12-Oct-2008)
SSD contains a file system with errors, check forced.
Error reading block 1020 (Attempt to read block from filesystem resulted in short read).  

SSD: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
fsck died with exit status 4

```
(I removed unnecessary lines)

Why is this happening?

I formated my SSD with this command:
mkfs.ext3 -m 0 /dev/sda1

Do I have to format my SSD in some special way? 

Thank you.

---

### Post by dcstar on 2009-03-31
> **LepeKaname said:**
> Ubuntu Intrepid(32b) 

Few weeks ago I bought a SSD disk of 32GB to store my important documents (because they are suppose to rarely fail). 
.......

SSD devices still have a finite quantity of write cycles - eventually they will all fail.

You seem to have one that has gone faulty very early.

---

### Post by LepeKaname on 2009-03-31
The strange thing is that I just copied my data there and I didn't use it at all... that is really bad....

---

### Post by kpatz on 2009-03-31
You got a defective one... that's what warranties (and backups) are for.  Return it, get another, and you should have better luck.

---

