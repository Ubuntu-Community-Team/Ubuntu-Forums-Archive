---
title: "HELI-X Model helicopter simulator"
date: 2008-05-26
forum: Gaming &amp; Leisure
---

### Post by Rofo on 2008-05-26
Hi:

I just want to know if someone has experience of installing and running the Linux version of HELI-X? It won't start on my (Ubuntu 7.10) system. JRE is updated to latest version.

---

### Post by lowkey3d on 2008-06-03
I also tried on Hardy without sucess

---

### Post by lowkey3d on 2008-06-06
Update. I just tried i386 version of Hardy and Heli-X starts.
previously I was using AMD64 version and there are issues with Java.
I just need to try to get the controller interface working.
No time a the moment to look at whats happening.

---

### Post by Sockerdrickan on 2008-06-06
cool I'm gonna try it out

---

### Post by lmorselli on 2008-10-13
I get it to run perfectly on Hardy
There will can be a problem with jinput, you can find a solution here:

[http://valentijn.sessink.nl/?p=16#more-16](http://valentijn.sessink.nl/?p=16#more-16)

Valentijn also has a good solution for running Hely-x faster by reducing the scenery jpegs.

Now I'm triyng to run it on Intrepid Ibex, all ok except the sound, due to a different version of OpenAL

Great simulator, tanks to Valentijn for the help.

---

### Post by lmorselli on 2008-10-13
> **lmorselli said:**
> 
Now I'm triyng to run it on Intrepid Ibex, all ok except the sound, due to a different version of OpenAL


Done.
Just remove libopenal.so in HELI-X/libs/joal/linux-i586 (or amd 64) and link make a link to /usr/lib/libopenal.so

cd HELI-X/libs/joal/linux-i586/
rm libopenal.so
ln -s /usr/lib/libopenal.so libopenal.so

And also the sound works.

Bye.

---

### Post by nossifer on 2011-06-24
Confirmed for demo of 3.0

edit:  Nutty Narwhal Kubuntu

---

