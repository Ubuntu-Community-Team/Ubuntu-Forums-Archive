---
title: "install .tar.bz2"
date: 2006-08-27
forum: Gaming &amp; Leisure
---

### Post by ksn linux on 2006-08-27
i have installed ut2004 and just downloaded the mega pack. it is a .tar.bz2 file is there some sort of special compiler i need to install the bonus pack? and if i don't, how do i do it in the first place i am pretty new to linux

---

### Post by Perfect Storm on 2006-08-27
tar.bz2 means there's some files compressed. It can contain everything. Luckly I have the mega-pack so I can help you there ;)
Did you installed ut2004 as default? (/usr/local/games). If so

unpack the tar.bz2 (right click, ectract here)
```
cd /into/unpack/folder
sudo cp -r * /usr/local/games/ut2004
```

done.

---

### Post by xander848 on 2006-08-27
Here's a link to something that will tell you how to install most anything. Bookmark it so you have it in case you dont know how to install a certian file.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by djuhl30 on 2007-05-20
[http://www.omgili.com/preview/aHR0cDovL2ZvcnVtcy5iZXlvbmR1bnJlYWwuY29tL3Nob3d0aHJlYWQucGhwP3Q9MTgyOTIz](http://www.omgili.com/preview/aHR0cDovL2ZvcnVtcy5iZXlvbmR1bnJlYWwuY29tL3Nob3d0aHJlYWQucGhwP3Q9MTgyOTIz)

You need to edit the ut2004 wrapper script to run the 64 bit binary after patching

---

### Post by Cappy on 2007-05-20
> **djuhl30 said:**
> [http://www.omgili.com/preview/aHR0cDovL2ZvcnVtcy5iZXlvbmR1bnJlYWwuY29tL3Nob3d0aHJlYWQucGhwP3Q9MTgyOTIz](http://www.omgili.com/preview/aHR0cDovL2ZvcnVtcy5iZXlvbmR1bnJlYWwuY29tL3Nob3d0aHJlYWQucGhwP3Q9MTgyOTIz)

You need to edit the ut2004 wrapper script to run the 64 bit binary after patching

There is an additional patch beyond the megapack for 64-bit. You'll need "3369-2" if you plan on running the 64-bit binary or else it may have problems.

---

