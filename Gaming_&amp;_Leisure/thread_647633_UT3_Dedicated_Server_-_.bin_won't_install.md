---
title: "UT3 Dedicated Server - .bin won't install?"
date: 2007-12-22
forum: Gaming &amp; Leisure
---

### Post by MotF Bane on 2007-12-22
Exactly what the thread title says.  I have a file on my desktop called "UT3-linux-server-12172007.bin", but it refuses to install when I click on it.  I tried opening a terminal window, and putting in "chmod a+x UT3-linux-server-12172007.bin", but it says something about file/directory not found, but the file is clearly sitting there.  Operating system is Ubuntu 7.10 64-bit.

---

### Post by cogadh on 2007-12-22
Did you "cd" to the Desktop directory before running the chmod command?

Also, you should run it from a terminal, not by double clicking:
```
cd Desktop
chmod +x UT3-linux-server-12172007.bin
./UT3-linux-server-12172007.bin
```

---

### Post by MotF Bane on 2007-12-22
CD Desktop got the chmod command to work, and now the file properties say that it is "application/x-executable", but the "./ut3-linux-server-12172007.bin" command gets a reply of "file/directory not found".  It can't be double-clicked on either, so it's basically a blob sitting on the desktop.

---

### Post by autocrosser on 2007-12-22
Take a look at Ryan's mailing list archives:  [http://icculus.org/cgi-bin/ezmlm/ezmlm-cgi?64](http://icculus.org/cgi-bin/ezmlm/ezmlm-cgi?64)

You should find the info/help there.

---

### Post by DoktorSeven on 2007-12-23
> **MotF Bane said:**
> CD Desktop got the chmod command to work, and now the file properties say that it is "application/x-executable", but the "./ut3-linux-server-12172007.bin" command gets a reply of "file/directory not found".  It can't be double-clicked on either, so it's basically a blob sitting on the desktop.

Case matters, if it's "UT3-(etc)" then ./ut3-(etc) won't work.  Tab completion helps (type part of it, hit TAB and it will try to complete the filename).

---

### Post by Ardrias on 2007-12-23
I thought he didnt make a 64-bit version of it?

---

### Post by angela159 on 2008-03-04
why install the server software if there isnt an client installer yet.

---

### Post by MotF Bane on 2008-03-04
Run the dedicated server on an older Linux box, and have a bunch of people connect to it with new Windows based gaming machines, and then none of them have to deal with server based slowdowns.

---

### Post by Jcarr_toonist on 2009-10-17
Bit of an old thread but the solution is installing the 32 bit binaries 

```
sudo apt-get install ia32-libs
```

---

