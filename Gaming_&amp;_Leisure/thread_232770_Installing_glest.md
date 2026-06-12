---
title: "Installing glest"
date: 2006-08-09
forum: Gaming &amp; Leisure
---

### Post by mikesena on 2006-08-09
I am having MAJOR troubles installing this.  First up, is there an easy installer (deb package) somewhere?!  I can't find any.

Second, the old deb i managed to find is saying 'Error:  Dependency not satisfiable: xlibs", or something along those lines.

How do I fix this problem?  xlibs-dev is installed

---

### Post by mongolito404 on 2006-08-09
A guy named David Gonzalez has made Glest 2.0 .deb packages (glest and glest-data) for Debian, you can get them on [his website](http://www.akurashy.com/glest_linux/), or simply```
wget http://www.akurashy.com/glest_linux/glest-data_1.9.99+2.0rc5-0buntu1_all.deb
wget http://www.akurashy.com/glest_linux/glest_2.0.0-0ubuntu1_i386.deb
dpkg -i glest-data_1.9.99+2.0rc5-0buntu1_all.deb glest_2.0.0-0ubuntu1_i386.deb
```

I installed glest using these package on my Ubuntu 6.06 LTS and it seems to work fine.

---

### Post by mikesena on 2006-08-09
wow thank you very much!  it worked perfectly to install

unfortunatly, i still get this error when the game tries to launch:

ALC_INVALID_DEVICE


is there a way to fix that?

---

### Post by mongolito404 on 2006-08-09
On the Ubuntu-fr forum, a user reports that he has to change the value of CheckGlCaps from 1 to 0 in glest.ini to make it works. It didn't have this problem and don't know where the glest.ini file is but it may help.

Also, googling for "ALC_INVALID_DEVICE site:glest.org" I found an [old board page from glest.org](http://72.14.221.104/search?q=cache:isTfJlpVhg4J:glest.org/board/viewtopic.php%3Fp%3D2597%26sid%3D025a7d0319612c848daccbbc75205184+ALC_INVALID_DEVICE+esd&hl=fr&gl=be&ct=clnk&cd=3&client=firefox) with the following advice:> If you have an ALC_INVALID_DEVICE error make sure that no software is grabbing your soundcard (typicall candidates are artsd/esd which are the kde/gnome sound daemons). If killing them won't help try upgrading your OpenAL version.

---

### Post by mikesena on 2006-08-09
i will have to check when i get home, i am currently out

---

### Post by mikesena on 2006-08-10
ive checked, and it didn't.  how do i update that library as you suggested?

---

### Post by onesojourner on 2007-01-23
that site is down is there a mirror some where?

---

### Post by jediborger on 2007-01-23
Well I couldn't find the debs but try this loki installer instead

[http://www.liflg.org/?catid=6&gameid=58]("http://www.liflg.org/?catid=6&gameid=58")

---

