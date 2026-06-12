---
title: "Startup programs?"
date: 2009-05-14
forum: General Help
---

### Post by ownaginatious on 2009-05-14
I'm actually running Debian, but it's similar enough that I thought I might be able to get some help here ;)

Anyway, I'm running a Debian web server that has both Apache2 and Apache Tomcat running on it, with a mod that "binds" them together. Right now, Apache2 is the only thing that automatically starts with the system.

I created a script in the /etc/init.d folder for tomcat and now I just need to have it start up with the system, but it's **very important** that it starts before apache2 for some reason.

Does anyone know how I would be able to add tomcat to the system start-up script before apache2?

Any help would be greatly appreciated.

Thanks,

Dillon

---

### Post by BslBryan on 2009-05-14
Hello, ownaginatious. :-)

How about pasting the script at the end of ```
/etc/init.d/rcS.sh
```

I think that will work.  

Keep me posted, and  best to you. :-)

---

### Post by HuckleSmothered on 2009-05-16
Find the script that starts Apache in the /etc/rcS.d. (or other rc_.d folders). It will have a number before it. S43portmap starts portmap. The Ks are for killing stuff. Make sure your script follows this convention and make the number before the Apache number. For instance, if I needed my own script to start before portmap, I would label it S40myscript.

---

