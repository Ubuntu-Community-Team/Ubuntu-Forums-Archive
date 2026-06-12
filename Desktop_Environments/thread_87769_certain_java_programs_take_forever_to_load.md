---
title: "certain java programs take forever to load"
date: 2005-11-08
forum: Desktop Environments
---

### Post by dafl00 on 2005-11-08
I've had a problem with certain java applications ever since I installed jre 1.5 

programs like azureus and limewire take forever to load.. there's no processing it just loads and sleeps for about five minutes before starting up.. 

has anyone ever heard of this problem?
```

$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

```

---

### Post by dafl00 on 2005-11-11
i'm glad to see i'm not alone 
[http://forum.java.sun.com/thread.jspa?messageID=3974132](http://forum.java.sun.com/thread.jspa?messageID=3974132) that person has the exact same problem too

i'm guessing the library is coded to look for something but it times out for me after 5 minutes... now i gotta look through java code.. jee that sounds like so much fun!!!!

---

### Post by coldrick on 2005-11-13
So did you install azureus etc after or before you installed jre1.5?

I have Azureus installed as well as jre1.5 (actually,  jdk1.5), and I have no such problem.

Startup shows:
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_05]
Configuring environment...
Loading Azureus:
etc.

Any possibility that you have some other java on the PATH (like the gcj one which causes all sorts of problems)?

Run Azureus from a terminal and see what appears.

Regards,
David

---

