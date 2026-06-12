---
title: "Repairing a RAR archive using files it contains"
date: 2009-06-08
forum: General Help
---

### Post by dr.koljan on 2009-06-08
There is a torrent where everyone is stuck at 99.8%. It contains a RAR archive that extracts successfully except one file which falls on the broken torrent block.

I have that file. In fact, I have all the files from the archive via a different source. Is it possible to "integrate" the file into the RAR archive so that the checksum doesn't fail and everyone can download the full archive?

---

### Post by stinger30au on 2009-06-08
you should be able to put he file in to the torrent directory and then do a check and it check the hash and say its ok and keep going

if it is located in a rar file. you need to extract the rar

add the file

recompress using the same compression and you should be right

---

### Post by Cheesemill on 2009-06-08
I personally don't think that this will work.

There is no guarantee that compressing a bunch of files twice will give you 2 identical compressed files with the same hash.

This is true of all compression programs (with the exception of torrentzip which was designed for just this purpose).

Cheesemill

---

### Post by dr.koljan on 2009-06-08
> **stinger30au said:**
> recompress using the same compression

That's the problem. I don't know what compression was used. If there is some way to find out, I'd be happy to know.

---

### Post by dr.koljan on 2009-06-08
No ideas?

I only need to replace one piece (2MB) of a 1.26GB file. There must be a way to do this. Is there really no way to find out what compression method was used?

---

### Post by DeMus on 2009-06-08
> **dr.koljan said:**
> No ideas?

I only need to replace one piece (2MB) of a 1.26GB file. There must be a way to do this. Is there really no way to find out what compression method was used?

With the rar files, there are no par2 files? Par2 files are made and normally also send with the rar files to repair incomplete rar files, or files which have been damaged during transmission.

---

### Post by dr.koljan on 2009-06-08
> **DeMus said:**
> With the rar files, there are no par2 files? Par2 files are made and normally also send with the rar files to repair incomplete rar files, or files which have been damaged during transmission.

There is no need for them in a torrent, as damaged pieces just get re-downloaded. However, no one has this piece in this case. What I need is basically to find out the compression settings used in the original archive.

---

### Post by Cheesemill on 2009-06-08
To reiterate what I posted above, knowing the compression settings **will not** help.

Even on identical machines with identical software versions compressing a bunch of files will give a different result **every time** (unless done using torrentzip).

Cheesemill

---

### Post by michy99 on 2009-06-08
Try this:```
rar v[t] yourarchive.rar
```This will list the files in the archive with information with includes the compression method of each file. Whether it will work for the incomplete file, or what to do with the information, I don't know.

---

