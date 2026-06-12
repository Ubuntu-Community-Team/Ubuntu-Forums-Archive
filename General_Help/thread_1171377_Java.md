---
title: "Java"
date: 2009-05-27
forum: General Help
---

### Post by demalan on 2009-05-27
I have ubuntu 9,04 and it is updated, but I have problems with Java. I want to use the trading platform from gt247.com. It runs on Java. When I try to install their platform, I get the message "with what application do I want to open the file" I suppose it must be Java, but I dont know where is Java to be found on my system.

---

### Post by hal8000 on 2009-05-27
I just visited that site and it appeared to work ok, if this is the URL:

[http://www.gt247.com/](http://www.gt247.com/)

At a terminal type
java -version

I have Jaunty installed and this is my version:
anc@orac:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)

If you get the same result then you will have to be more specific about what file you are opening on that site

---

### Post by SOULRiDER on 2009-05-27
Make sure you ahve these packages installed:
```
sun-java6-jre
sun-java6-plugin
```

---

