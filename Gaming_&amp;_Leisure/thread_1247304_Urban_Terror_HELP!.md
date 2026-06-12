---
title: "Urban Terror HELP!"
date: 2009-08-22
forum: Gaming &amp; Leisure
---

### Post by SNOOPY817 on 2009-08-22
Okay well, I'm a noob first of all, and i just downloaded urban terror:

UrbanTerror_41_FULL.zip

And idk how to install it or the commands on terminal or nothing, so i would
really appreciate it if some one helped me. :D
thanks.

---

### Post by maxbaldwin on 2009-08-22
First of all, extract the file.
```
unzip /path/to/Urban_Terror_41_Full.zip
```

Secondly, you'll need to figure out your architecture.
```
uname -m
```

Thirdly, you need to make the right file executable.

So, if you're on an x86 architecture machine, you will need to run:
```
chmod +x /path/to/Urban_Terror_41_Full/ioUrbanTerror.i386
```

...and if you're on an x64 architecture or whatever, you'll need to do:
```
chmod +x /path/to/Urban_Terror_41_Full/ioUrbanTerror.x86_64
```

To run the game, cd to the Urban_Terror_41_Full directory, and do this to the appropriate file:
```
./ioUrbanTerror.$arch
```
Where $arch == your architecture. i386 or x86_64.

---

### Post by Bonster on 2009-08-22
Right click on the i386 or x64 file depending on ur OS. Then go properties, In the permission tab, check Allow Executing and thats it now just double click on the file and u can play it

---

### Post by SNOOPY817 on 2009-08-22
> **Bonster said:**
> Right click on the i386 or x64 file depending on ur OS. Then go properties, In the permission tab, check Allow Executing and thats it now just double click on the file and u can play it
Thanks bro, yours worked best :D

---

