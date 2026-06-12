---
title: "CD burning problems"
date: 2006-02-21
forum: Desktop Environments
---

### Post by jimw on 2006-02-21
I'm using Ubuntu 5.10.

I've been trying to back upo my data files, first off using K3B.

The biggest problem I had was that certain combinations of files (very many files, though never numbering more than 500Mb),  would give the error on K3B, "unable to calculate the final file size."

The debugging info said :

System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
HIGH SPEED CD ROM YSQQ (/dev/hdb, ) at /media/cdrom0 [CD-ROM] [CD-ROM] [None]

SONY CD-RW  CRX230EE 2YS1 (/dev/hdc, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]
K3b
-----------------------
Size of filesystem calculated: 0

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv

mkisofs
-----------------------
Rock Ridge signatures found
Incorrectly encoded string (h&#65533;z%.html) encountered.
Possibly creating an invalid Joliet extension. Aborting.

msinfo
-----------------------
0,11702

msinfo command:
-----------------------
/usr/bin/cdrecord.mmap dev=/dev/hdc -msinfo 

I did manage to get certain bits and pieces of the data backed up.

Tonight, searching for help on the list, I didn't come across my specific problem, but I did find mention of CDCreator, which seems a lot easier.  I tried the troublesome file-group, and got the message "some files appear to have invalid file names."

Unfortunately, this tells me nothing useful.  

Taking the total error message to Google got me no hits, taking the important part, "invalid file names," got me several million, none of the first few seeming to have any connection with my difficulty, or indeed with Ubuntu at all.

Can anyone help me out here?

Thanks

JimW

---

### Post by suRoot on 2006-02-21
Whey not try gnomebaker?  I've found K3B to be troublesome at times.

```
sudo apt-get install gnomebaker
```

Regarding the invalid file names, it probably has to do with the format the other program was trying use to write the CD.  Some formats have limitations on file names (for example, long file names are a problem).

---

### Post by frodon on 2006-02-21
Go in the advanced options in the k3b burning window and allow long file names and special characters like "~ #"
Your problem should be only with the file name and the default option of k3b about file names (it don't allow special characters by default like many other burning softwares).

---

