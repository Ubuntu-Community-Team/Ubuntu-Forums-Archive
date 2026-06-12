---
title: "Broken packages?"
date: 2006-03-02
forum: Desktop Environments
---

### Post by Matthai on 2006-03-02
I tried to install cinelerra and avidemux todaj. One week ago everything went fine, but today...

For installing Cinelerra I added this repositories into sources.list:

#Cinelerra
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main
deb [http://www.kiberpipa.org/~gandalf/ubunt](http://www.kiberpipa.org/~gandalf/ubunt) … mjpegtools ./
deb [http://www.kiberpipa.org/~gandalf/ubunt](http://www.kiberpipa.org/~gandalf/ubunt) … /pentium4/ ./

sudo apt-get update

sudo apt-get install cinelerra

This package does not exists anymore: libraw1394-8 


And Avidemux:

sudo apt-get install avidemux

This package does not exists anymore: libfaac0 (>= 1.24-0.4) 

Any help?

---

### Post by jon_gunnar on 2006-03-02
[QUOTE=Matthai]I tried to install cinelerra and avidemux todaj. One week ago everything went fine, but today...

For installing Cinelerra I added this repositories into sources.list:

#Cinelerra
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main
deb [http://www.kiberpipa.org/~gandalf/ubunt](http://www.kiberpipa.org/~gandalf/ubunt) … mjpegtools ./
deb [http://www.kiberpipa.org/~gandalf/ubunt](http://www.kiberpipa.org/~gandalf/ubunt) … /pentium4/ ./

sudo apt-get update

sudo apt-get install cinelerra

This package does not exists anymore: libraw1394-8 


And Avidemux:

sudo apt-get install avidemux

This package does not exists anymore: libfaac0 (>= 1.24-0.4) 

Any help?[/QUOTE]

After the apt-get update did you do a:
apt-cache search libraw ex.?

It looks like apt says plainly that those packages is gone.
But I dont use those repositories so its a little guess.

---

### Post by Matthai on 2006-03-03
Yes, that is exactly the problem - packages does not exists anymore. And I have no idea what to do in such a case. Who to inform...?

---

### Post by wh0rd on 2006-04-12
The same issue here!

---

