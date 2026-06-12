---
title: "problems with CREATIVE NX webcam"
date: 2006-02-01
forum: Desktop Environments
---

### Post by crixtiano on 2006-02-01
Hi, i'm having a problem with creative NX webcam.

Old I used it in linux of normal form.  But recently, I had to format the PC and I installed the Breezy again.  When installing my webcam again, it did'nt work.  Look , I did it:

============================================
I acess [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) and I downloaded the file spca5xx-20050906.tar.gz.



$ tar -xzvf spca5xx-20050906.tar.gz

cd spca5xx-20050906
$ make

$ sudo su -

# make install

# modprobe usbcore

# modprobe spca5xx

# apt-get install camstream


To detect the webcam:

$ caminfo
$ camstream
============================================

The last command stop the system. The software camstream open in Gnome, but when I choice to see the webcam windows, the PC stops 100%.

So, how to install CREATIVE NX right?

I'm using this version of kernel and gcc:

============================================
$ uname -r
2.6.12-9-386

$ gcc --version
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. 
============================================


10ks.


Cristiano M. Magalhães

---

### Post by ranf on 2006-02-01
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=75284&highlight=spca](http://ubuntuforums.org/showthread.php?t=75284&highlight=spca)

---

### Post by crixtiano on 2006-02-01
hi, 

10ks. The webcam is working now!

:-)

---

### Post by crixtiano on 2006-02-02
hi, my webcam works fine for a time, but a few minutes later, it stops the system again.

---

