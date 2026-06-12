---
title: "How do I set up java env vars?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by [censored] on 2005-11-06
Hi. What's the best way, in ubuntu, to set up the java environment.

I have installed sun-j2re1.5 using apt-get. 

I have added the following lines to /etc/bash.bashrc

> 
export JAVA_HOME=/usr/lib/j2re1.5-sun
PATH=$PATH:/usr/lib/j2re1.5-sun/bin


Now I find that java apps run fine, if I execute them from the command line. But ... if I try to execute them using a desktop icon in gnome, or via the applications menu, nothing happens. :(

What do I need to set up?

---

### Post by coldrick on 2005-11-06
That's odd. What do you see if you type "java -version" - without quotes - in a terminal window?

Regards,
David

---

### Post by jvictor on 2005-11-06
edit ur path from PATH=$PATH:/usr/lib/j2re1.5-sun/bin

to 

export PATH=/usr/lib/j2re1.5-sun/bin:${PATH}

it'll work

---

### Post by [censored] on 2005-11-07
coldrick 

> 
$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)


---

### Post by [censored] on 2005-11-07
[QUOTE=jvictor]edit ur path from PATH=$PATH:/usr/lib/j2re1.5-sun/bin

to 

export PATH=/usr/lib/j2re1.5-sun/bin:${PATH}

it'll work[/QUOTE]

Nope. Just rebooted, with my /etc/bash.bashrc modified as above, still have the same problem. Thanx anyway. :(

---

