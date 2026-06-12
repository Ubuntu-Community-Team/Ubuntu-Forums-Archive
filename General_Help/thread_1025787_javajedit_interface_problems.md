---
title: "java/jedit interface problems"
date: 2008-12-30
forum: General Help
---

### Post by Virtual DarKness on 2008-12-30
recently something changed and now I get some strange extra spaces in the jEdit interface:

[[IMG]http://img70.imageshack.us/img70/1592/jeditgl5.th.png[/IMG]](http://img70.imageshack.us/my.php?image=jeditgl5.png)

While it should be like in this screenshot:
[http://www.jedit.org/jedit-snap-34.png](http://www.jedit.org/jedit-snap-34.png)

I've tried to reset the jEdit prefs to see if that was the cause but also with a "fresh install" I still get that error.. The version of jEdit is the same so maybe the problem is due to some software I installed recently or to software updates.. :confused: anyway it seems to be more a problem with the java environment that with jEdit itself..

do you have any idea about how I could fix it?

thanks.

bye,
Giovanni.

---

### Post by Virtual DarKness on 2008-12-30
Using galternatives I saw that the java settings was set to:

> /usr/lib/jvm/java-6-openjdk/jre/bin/java

instead of
> /usr/lib/jvm/java-6-sun/jre/bin/java

..changing it fixed the problem.. anyway I was quite sure I was using the second one but wanted to checked it anyway and saw that the problem were caused by the openjdk version.. 

bye,
Giovanni.

---

