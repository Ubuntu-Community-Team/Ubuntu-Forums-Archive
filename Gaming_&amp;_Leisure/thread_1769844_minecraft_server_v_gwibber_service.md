---
title: "minecraft server v gwibber service"
date: 2011-05-28
forum: Gaming &amp; Leisure
---

### Post by wog on 2011-05-28
I have a minecraft server.

I started looking for things creating lag and discovered gwibber-service was on a lot. I don't use gwibber so I uninstalled it, but gwibber-service continued to run until I killed it.

But now I can't link to my minecraft server.

Can some kind person out there help me with the basics of setting up a minecraft server, just to make sure it's not my setup being the problem and not the recent patch?

---

### Post by Ausmosis on 2011-05-31
> **wog said:**
> I have a minecraft server.

I started looking for things creating lag and discovered gwibber-service was on a lot. I don't use gwibber so I uninstalled it, but gwibber-service continued to run until I killed it.

But now I can't link to my minecraft server.

Can some kind person out there help me with the basics of setting up a minecraft server, just to make sure it's not my setup being the problem and not the recent patch?


Howdy,

I have a minecraft server running flawlessly after watching this tutorial [http://www.youtube.com/watch?v=amiwO6PFFBQ](http://www.youtube.com/watch?v=amiwO6PFFBQ) 

The tutorial is for OSX however can be used for Linux. There is some stuff on an OSX Portmap application but you can skip past it. You will also have change the following details in the bash script so that Linux understands:

Change the following line:

```
java -Xmx1G -Xms1G -jar minecraft_server.jar
```

To the following:

```
java -Xmx1024M -Xms1024M -jar minecraft_server.jar
```

Have a crack at it and let me know how you go.

Ausmosis

---

