---
title: "HowTo run eclipse"
date: 2005-03-28
forum: Desktop Environments
---

### Post by illmonkey on 2005-03-28
Hello,

I downoaded eclipse-SDK-3.0.2-linux-gtk.zip extrat it and try to run startup.jar by using java -jar startup.jar on the the terminal... But it doesn't work

[email]root@ubuntu:/home/illmonkey/Desktop/eclipse-SDK-3.0.2-linux-gtk.zip[/email]_FILES/eclipse # java -jar startup.jar
Failed to load Main-Class manifest attribute from
startup.jar

It doesn't work :( please explain me how to run eclipse ..

I installed this version of java

[email]root@ubuntu:/home/illmonkey/Desktop/eclipse-SDK-3.0.2-linux-gtk.zip[/email]_FILES/eclipse # java -version
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)

thank you so much :)

---

### Post by Leif on 2005-03-28
I run it by calling "eclipse". no java -jar. So if you put it in opt, /opt/eclipse/eclipse.

---

### Post by illmonkey on 2005-03-28
it works it's ok! 

:)

---

### Post by neshaug on 2005-04-02
I cant get eclipse to work...

If I try to start it from the console I get:

GTK-Warning: can not open display

Ive installed java, but I think my paths are screwed and I dont know how to fix It cause Im a noob :P

---

### Post by Leif on 2005-04-03
OK, if you tried to manually install java, I recommend that you delete it and retry with the first method described here :

[http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

After that, download the latest eclipse, unpack it to /opt, and try again. It really should be quite painless.

---

### Post by neshaug on 2005-04-03
thanks leif, that worked out fine! Eclipse got a little heavy on my laptop though. Specialy when I tries to list all the functions avaliable under each category etc.. Going to try emacs now.

---

