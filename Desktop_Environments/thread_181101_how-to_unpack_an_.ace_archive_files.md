---
title: "how-to unpack an .ace archive files"
date: 2006-05-23
forum: Desktop Environments
---

### Post by songo on 2006-05-23
hi there...
i got this ace packed album from aMule and know i dond't know what to do with it. how do i unpack a .ace archive?

tanx

---

### Post by Jussi Kukkonen on 2006-05-23
[QUOTE=songo]hi there...
i got this ace packed album from aMule and know i dond't know what to do with it. how do i unpack a .ace archive?
[/QUOTE]

```
sudo apt-get install unace
unace x <archive.ace>
```
should do it.

---

### Post by songo on 2006-05-23
just to report. I got the error below, because the version in the repositoires is out of date. i tried with the [latest version 2.5]("http://www.winace.com/files/linunace25.tgz") on[ www.winace.com]("http://www.winace.com/") and it works fine. thanks

$ unace x archive.ace
UNACE v1.2    public version

Processing archive: archive.ace


file1.mp3
 Extracting
File compressed with unknown method. Decompression not possible.

Error occurred

---

### Post by mayonesiac on 2006-07-04
have the same problem

---

### Post by lashbam on 2007-02-05
me too

---

### Post by glotz on 2007-02-05
How about you guys try the same solution?

---

### Post by jjalocha on 2007-12-04
You might try 'unace-nonfree' instead of 'unace'. According to the documentation, 'unace' supports only ACE 1.0 archives, while the non-free package supports all current ACE archives.

I don't know in (K)Ubuntu, but in Xubuntu, it is not necessary to run the command line program. You just can double-click the file in the file-manager, and archive-manager pops up and handles the extraction.

---

### Post by therecanbeonlyonept on 2008-07-12
Or you may want to install wine and than install winace.

It works 100% here. I can compress and extract this way.:)

---

### Post by pfluegl on 2008-07-21
You can use File Roller (which is what Xubuntu file manager uses) to uncompress the file. 

file-roller somefile.ace

---

