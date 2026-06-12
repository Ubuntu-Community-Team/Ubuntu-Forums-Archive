---
title: "Got the best Christmas Gift ever. :D"
date: 2011-12-25
forum: Gaming &amp; Leisure
---

### Post by TheNerdAL on 2011-12-25
I never got what I wanted and my friend knew that I wanted the Humble Indie Bundle #4 games and she gave me the gift of that. :D

Problem is that they're in tar.gz files and I don't know how to install those. xD

---

### Post by user1397 on 2011-12-25
An easy way to install packages from source is through a program called checkinstall, which makes the source files into a .deb which you can uninstall easily afterwards. First install the package checkinstall ```
$ sudo apt-get install checkinstall
```

Extract the .tar.gz archive, then open a terminal and go into the directory where the unpacked folder is ```
$ cd /path/to/folder/
``` then do ```
./configure
make
sudo checkinstall
```and voila

---

### Post by TheNerdAL on 2011-12-25
> **ubuntuman001 said:**
> An easy way to install packages from source is through a program called checkinstall, which makes the source files into a .deb which you can uninstall easily afterwards. First install the package checkinstall ```
$ sudo apt-get install checkinstall
```

Extract the .tar.gz archive, then open a terminal and go into the directory where the unpacked folder is ```
$ cd /path/to/folder/
``` then do ```
./configure
make
sudo checkinstall
```and voila

I shall try that! There's one game that's a .zip too and one that's a .sh.

---

### Post by wolfen69 on 2011-12-25
For the .sh file, just do (assuming it is in your Home folder)
```
sudo sh name_of_file.sh
```

---

### Post by undecim on 2011-12-25
All the tar.gz files in HIB 4 are either install binaries (in which case, just run them in a terminal), or precompiled files. For the latter (i.e. when there is more than one file in the tar.gz) just copy them to somewhere in your home directory and run the binary file inside the folder (e.g. by double-clicking it). The binary file is usually an extensionless file with the same name as the game. Some of them have x86 or x86_64 at the end for 32-bit and 64-bit systems respectively.

If you have any problems with running a specific game, let me know and I can give you precise instructions.

---

### Post by TheNerdAL on 2011-12-25
Super Meat Boy is going to make me rage. D:

---

### Post by oldos2er on 2011-12-26
Moved to Gaming & Leisure.

---

### Post by TheNerdAL on 2011-12-26
I'm still confused on how to install this tar.gz file: 

```
nightskyhd-linux-1324519044.tar.gz
```

---

### Post by Perfect Storm on 2011-12-28
> **TheNerdAL said:**
> I'm still confused on how to install this tar.gz file: 

```
nightskyhd-linux-1324519044.tar.gz
```

Just unpack it, go to linux folder and double-click on the binary to play.

---

### Post by Rustybolts on 2011-12-28
Right click the file, select extract here.

---

