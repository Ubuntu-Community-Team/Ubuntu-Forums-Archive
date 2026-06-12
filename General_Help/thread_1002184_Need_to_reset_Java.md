---
title: "Need to reset Java"
date: 2008-12-04
forum: General Help
---

### Post by Split-Skreen on 2008-12-04
Alright so I'm relatively new to linux but I have come a long way to understand its basics concepts in the past little while. Right now I've got most things working but I believe I have messed up my Java installations. I think, due to my trial and error methods, that I have installed some portions of Java 6 while still relying on the older portions of Java 5.

Basically I would like to completely reset all of my Java plugins, and various subsidies back to the native ubuntu 8.10 settings and then upgrade them properly. 
Any help here would be marvellously appreciated.
Cheers!

---

### Post by taurus on 2008-12-04
Just install version 6 with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by Split-Skreen on 2008-12-04
Thanks, This was the output after that process

java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)

However I am concerned this didn't change anything because of the line:
Java HotSpot(TM) Client VM (build 11.0-b15,**_ mixed mode_**, sharing)

---

### Post by taurus on 2008-12-04
I have the mixed mode with my version too.

```

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```

Otherwise, use synaptic and remove the older version, 5, if you have it installed.

---

### Post by Split-Skreen on 2008-12-04
Thanks for your help with this but I still believe there is something amiss with my java. I tested youtube (which has been messing up on me lately) and it locks up firefox when I load any videos. I also am having an audio dilemma with tuxguitar that I believe is java related.

Thoughts?

---

### Post by taurus on 2008-12-04
From the address field of firefox, type

```
about:plugins
```
and see which version of java plugin firefox is using.

---

### Post by Split-Skreen on 2008-12-04
This was what it had for the java plug-in
Java(TM) Plug-in 1.6.0_10-b33

I was reading on a few other threads and forums, according to some, Firefox is apparently having issues with flash lately. Though I can't see why that would be the case...perhaps I need to upgrade my firefox... I'm going to look into that right now.

---

