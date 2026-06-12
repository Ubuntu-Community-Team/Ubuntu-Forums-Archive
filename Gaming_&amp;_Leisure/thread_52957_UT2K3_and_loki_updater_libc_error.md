---
title: "UT2K3 and loki updater libc error"
date: 2005-07-29
forum: Gaming &amp; Leisure
---

### Post by CiberAmigo on 2005-07-29
I have installed UT2K3 and tried to update it with loki_updater, but I get an error:

cannot handle file 'libc.so.6' with TLS data
The program returned an error code (1)
Update failed
 :? 

I have looked around Ubuntu forum, and cannot find enything specific on this issue. Allthoung I have discovered that many of you have UT2K3 running so I hope that some of you can tell me how to make it function.

I use KDE and Geforce FX5200 AMD CPU and have 1GB RAM.

 :grin:  :grin: 

CiberAmigo

---

### Post by ubuntu_demon on 2005-08-02
you posted in the wrong forum. That's why I moved it.

---

### Post by CiberAmigo on 2005-08-07
I'm sorry I posted it in the wrong forum  and thanks for moving it.

CiberAmigo

---

### Post by ubuntu_demon on 2005-08-08
[QUOTE=CiberAmigo]I'm sorry I posted it in the wrong forum  and thanks for moving it.

CiberAmigo[/QUOTE]
 np :)

try this :
$ sudo apt-get install libc6

---

### Post by CiberAmigo on 2005-08-11
jan@Linux:~ $ sudo apt-get install libc6
Password: **********
Reading packagelists  ... Done
Building dependencies  ... Done
libc6 is the newest version.

(I tranlated this from the output in my native language), so it won't help much since i need version 2.3.2.ds1-21ubuntu13 and only have 2.3.2.ds1-20ubuntu13.
I don't think the deveopers have finished version 2.3.2.ds1-21, because I have seen others with libc6 issues. but I can live with that since I use Ubuntu.

I have fixed my loki update problem, by manually copying all the files from the UT2003 patch 2225 (tar arcivefile), instead of using the loki updater.

Thank for the help!  :) 

CiberAmigo

---

### Post by ubuntu_demon on 2005-08-11
[QUOTE=CiberAmigo]jan@Linux:~ $ sudo apt-get install libc6
Password: **********
Reading packagelists  ... Done
Building dependencies  ... Done
libc6 is the newest version.

(I tranlated this from the output in my native language), so it won't help much since i need version 2.3.2.ds1-21ubuntu13 and only have 2.3.2.ds1-20ubuntu13.
I don't think the deveopers have finished version 2.3.2.ds1-21, because I have seen others with libc6 issues. but I can live with that since I use Ubuntu.

I have fixed my loki update problem, by manually copying all the files from the UT2003 patch 2225 (tar arcivefile), instead of using the loki updater.

Thank for the help!  :) 

CiberAmigo[/QUOTE]
 np :)

breezy has a newer libc6 (but you can't use that one easily in hoary)
the current breezy libc6 version is : 2.3.5-1ubuntu7

---

### Post by CiberAmigo on 2005-08-29
I then look forward to the realease of the breezy

Cencerly
CiberAmigo

---

