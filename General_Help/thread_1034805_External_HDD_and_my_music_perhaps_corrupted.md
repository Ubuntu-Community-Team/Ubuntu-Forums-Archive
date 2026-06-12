---
title: "External HDD and my music perhaps corrupted?"
date: 2009-01-09
forum: General Help
---

### Post by skizeee on 2009-01-09
Hi

I dont know what is happening here...

Lent my HDD to my friend who also runs Ubuntu (both of us are noobs). The HDD has music and other files on it. My friend had a external screen resolution problem and to fix this I think he pressed ALT+f4 which fixed the screen, but appears to have lokced us out of my HDD. My Macbook can find the other files but cant access the music on it anymore...

Is the drive locked little padlocks appear on the folders in ubuntu but not on MAC.

Is the data corrupted/deleted/locked? 

If someone could suggest where to start diagnosing would be great...

---

### Post by nothingspecial on 2009-01-09
First. If you type ```
gksudo nautilus
``` can you access the drive then?

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by blazemore on 2009-01-09
Go to a terminal and run:
```
sudo mount -a -o force
```

---

### Post by skizeee on 2009-01-09
Hi guys I was able to get into the drive using the forced mount and gksudo command now that Im in and able to open my music folder but there is nothing in there, however the HDD is reading 189GB free as it has always done...

---

### Post by blazemore on 2009-01-09
Use the terminal to cd to the folder in question. Type ls and see if you get a list of files.

---

### Post by jsroth on 2009-01-09
In case of a still installed Windows system and a NTFS partition I made some good experiences with just booting Windows, accessing the HDD/partition once and then umounting/ejecting it in Windows and booting Ubuntu/Linux again.

---

### Post by adamlau on 2009-01-09
(Re)take ownership of and reset permissions on your external HDD partition(s).

---

