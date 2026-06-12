---
title: "help installing a tar.bz2"
date: 2009-03-12
forum: General Help
---

### Post by mikeonthebeach on 2009-03-12
i need help installing a game called super mario clone fx 1.1 for ubuntu 8.10. the file is a tar.bz2 is there anyway to auto install this? i have no idea how to install this can some1 plz help me

---

### Post by zvacet on 2009-03-12
In the directory where you downloaded package run from terminal

```
tar jxvf super mario clone fx 1.1
```

That will created folder.Inside look for **install file** or **read me** file.That files will explain to you what to do next.

---

### Post by mikeonthebeach on 2009-03-12
im trying to install the game super mario clone fx 1.1 . the file type is a tar.bz2  i have no idea how to install this can some1 please help

---

### Post by overdrank on 2009-03-12
Threads merged. :)

---

### Post by oldos2er on 2009-03-12
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by mikeonthebeach on 2009-03-12
i followed the instructions from the link and i got to the part of where i extracted the folder from the package. there are no readme or install files, there is just a control.tar.gz, a data.tar.gz and a debian-binary

---

### Post by oldos2er on 2009-03-13
Do you have a URL for this? I'll take a look at it.

---

### Post by mikeonthebeach on 2009-03-13
[http://www.secretmaryo.org/index.php?page=game_downloads&sid=?sid=](http://www.secretmaryo.org/index.php?page=game_downloads&sid=?sid=)

---

### Post by taurus on 2009-03-13
Did you download the smc-1.7.tar.bz2 version?  After unpacking it, cd to smc-1.7 and you need to build it.

```
./configure
```
However, you probably need to install libboost-filesystem first since it will complain about it.  And of course, you have to install other libraries if ./configure can't find them on your machine.  Once ./configure is happy about it, then run

```
make
sudo make install
```

---

### Post by oldos2er on 2009-03-14
What Taurus said. The program requirements are in smc-1.1/doc/readme-linux.txt .

---

### Post by perrti-y02 on 2009-03-14
You say there is a debian binary. Do you mean a file with .deb on the end? if so just right click and open with gdebi package manager(or installer I forget what it is called)

---

