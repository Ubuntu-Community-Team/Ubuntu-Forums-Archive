---
title: "Classpath"
date: 2007-10-19
forum: Desktop Environments
---

### Post by DagonX on 2007-10-19
I am trying to set the CLASSPATH variable. 

CLASSPATH1=/usr/lib/jvm/java-6-sun-1.6.0.00/db/lib/derby.jar:$CLASSPATH
export $CLASSPATH

in /etc/profile. When I reboot and type $CLASSPATH in a terminal I don't get the classpath I set.

What do I need to do to set the $CLASSPATH. I am programming in Java and not having CLASSPATH set is causing me grief.

Charles

---

### Post by britishbulldog on 2007-10-29
To set a variable you can simply export it like this:

export CLASSPATH=$CLASSPATH:/usr/lib/jvm/java-6-sun-1.6.0.00/db/lib/

Remember it's a path so you don't want to add filenames in that path (shown in your example).

If you set the variable manually, it will require you to reset it every time you reboot.
If you want it to be set automatically you can add it to your ~/.profile or your ~/.bashrc

I hope this helps. :)

---

