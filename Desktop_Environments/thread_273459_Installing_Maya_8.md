---
title: "Installing Maya 8"
date: 2006-10-08
forum: Desktop Environments
---

### Post by v8YKxgHe on 2006-10-08
Hey,

I have Autodesk Maya 8 for Linux the only problem is it's all RPM packages and I don't know how to install them! This is what the instructions say:

```
rpm -i Maya-8.0-#.i686.rpm AWCommon-10.#.i686.rpm AWCommon-server-10.#.i686.rpm
```

But when I do that ( with sudo ) I get this error:

```
alex@alex-ubuntu:/media/cdrom0$ sudo rpm -i Maya8_0-8.0-163.i686.rpm AWCommon-10.80-12.i686.rpm AWCommon-server-10.80-12.i686.rpm
error: Failed dependencies:
        /bin/sh is needed by Maya8_0-8.0-163.i686
        /bin/sh is needed by AWCommon-10.80-12.i686
        /bin/sh is needed by AWCommon-server-10.80-12.i686
alex@alex-ubuntu:/media/cdrom0$

```

I am also running XGL/Compiz ( I havn't upgraded to Beryl, still on the last Compiz version ) if that makes any difference ( Since the viewports will be using OpenGL to )

Anyhelp would be great!

---

### Post by ThunderTor on 2006-11-15
Hi, Dont know if you have figured it out already, but I installed maya 8 using the same instructions as in the 7.0 install howto. 
[http://ubuntuforums.org/showthread.php?t=66859&highlight=maya](http://ubuntuforums.org/showthread.php?t=66859&highlight=maya)

I recomend changing you window behavior from alt+lclk to super (window key) or using the rotate view shortcut moves the entire window around. 

I just installed beryl 0.1.1 yesterday and although its quite cute and fun, I keep getting total system crashes after running beryl and maya for a minute of two, I have no stability issues running in regular metacity and I dont start beryl with my X session (I launch it from a program icon I made, since It is still a bit off from "stable").

---

