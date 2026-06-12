---
title: "Ubuntu 64 no Java Firefox plugin"
date: 2010-09-24
forum: Desktop Environments
---

### Post by n1unqn on 2010-09-24
Ubuntu Desktop 10.04 64 no Java Firefox plugin

sudo apt-get install sun-java6-plugin

gets

Couldn't find package sun-java6-plugin

:mad:

---

### Post by PRC09 on 2010-09-24
I believe you have to enable the Partner repos in System > Admin > Software Sources  > Other Software and reload and then try the command.....

---

### Post by n1unqn on 2010-09-24
Thank you this works...

   1. Enable repository: Click System -> Administration -> Software Sources, go to tab Other Software and tick the first entry ("partner"). Close and confirm the "Reload".
   2. Install Sun Java: Go to Applications -> Software-Center -> Search for "sun java" and install the first package ("Sun Java 6.0 Plugin"). You are done!

Someone needs to update the help file in ubuntu with this info. :popcorn:

---

### Post by kaspar_silas on 2010-09-29
Is that version actually working for you? 

I installed it and then done tests (using both firefox and chromium) at

[http://www.javatester.org/version.html](http://www.javatester.org/version.html)
and 
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

These told me all was okay and I was using:

Vendor: Sun Microsystems Inc. 
Version: Java 6 Update 18 
Operating System: Linux 2.6.32-25-generic
Architecture: amd64

All good so far. However when I try other sites like, say:
[http://processing.org/learning/basics/translate.html](http://processing.org/learning/basics/translate.html)

all I get is a gray box 

and on firefox
Start: applet not initialized in the bottom corner of firefox.

---

### Post by kaspar_silas on 2010-10-25
I worked out my problem. It seems the icetea and java plugins were not playing together nicely. 

I removed all the icetea stuff and now it seems all good.

---

### Post by frank4360 on 2010-10-26
I use on-line money transfers and the screen I use has Java applets.

Every time I update Ubuntu to the latest release the Java applet stops working - so I do not update Ubuntu on each release. Currently I am on 10.04.

BUT - although I always delete any Icedtea software through the Synaptic Package Manager, this time the Java applet still does not work. The required form appears for a few seconds then disappears!

I wonder if anyone else has a similar problem?

I am using a PackardBell laptop with 2 AMD Turion 64 processors and Ubuntu 10.04.

---

### Post by kaspar_silas on 2010-10-27
Silly question this but have you tried removing all Java then reinstalling.

---

