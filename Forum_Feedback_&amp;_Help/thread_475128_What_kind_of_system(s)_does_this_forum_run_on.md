---
title: "What kind of system(s) does this forum run on?"
date: 2007-06-15
forum: Forum Feedback &amp; Help
---

### Post by Golyadkin on 2007-06-15
I just wondered, with the amount of visitors these forums get, and the use of Ajax and loads of nice CSS and HTML, the speed is still so incredibly good.

If possible, maybe someone can share a little info about the hardware and software of these forums? It has to run Ubuntu ofcourse ;)

---

### Post by aks44 on 2007-06-15
Dude, your own browser tells you many things on the software used :

Apache/2.0.55 (Ubuntu)
PHP/5.1.2
vBulletin 3.6.7

---

### Post by Adamant1988 on 2007-06-15
I believe this is all hosted on Canonical's servers, or that canonical is donating the server space for it on a dedicated server.  Either way... the forums haven't always been this fast...

---

### Post by vexorian on 2007-06-15
I considered it was odd that vBulletin was used since it is not open source :) but it is very good, I use it in my site and it is very flexible on customizing and optimizing an example would be this cute Human theme for vBulletin they are using.

---

### Post by Golyadkin on 2007-06-16
> **aks44 said:**
> Dude, your own browser tells you many things on the software used :

Apache/2.0.55 (Ubuntu)
PHP/5.1.2
vBulletin 3.6.7

Yes, ofcourse I know this :) But that doesn't really give the speed. I am more interested in the kind of hardware and the configuration of it.

---

### Post by bapoumba on 2007-06-16
Thread moved to "Forum Feedback & Help".

---

### Post by ubuntu-geek on 2007-06-16
We have 2 servers :)

Web/Searching: 
(2) AMD Opteron(tm) Processor 280 (dual core)
16GB ram
500GB storage

Database:
(2) AMD Opteron(tm) Processor 280 (dual core)
8GB RAM
140GB Storage

Both run Ubuntu :)

---

### Post by Golyadkin on 2007-06-16
Wow :) sweet...

I already had an idea this had to run on some serious hardware, thanks for sharing Ryan!

With 16GB of RAM, do you still use swap space? And if you would, does it help to put the swap partition on a RAID array?

---

### Post by ubuntu-geek on 2007-06-16
We don't swap really these days back over a year ago we did and yeah it helped. Since moving all the search functions over to [sphinxsearc]("http://www.sphinxsearch.com")h things have improved :)

---

### Post by FuturePilot on 2007-06-17
No wonder why this forum is so fast. It's 
[IMG]http://static.flickr.com/83/214998683_bd3c9a35b5_o.jpg[/IMG]
:D

---

### Post by Golyadkin on 2007-06-17
Alright, I have been playing with MySQL's fulltext search and that has worked for me fine. (However, I only get a few visitors :))

The first time I searched the forums here I thought it wasn't working, because I got my results so fast. (Nothing found) :D

---

