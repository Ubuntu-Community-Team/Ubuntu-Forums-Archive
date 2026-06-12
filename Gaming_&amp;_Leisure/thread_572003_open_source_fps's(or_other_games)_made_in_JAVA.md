---
title: "open source fps's(or other games) made in JAVA?"
date: 2007-10-09
forum: Gaming &amp; Leisure
---

### Post by Juco on 2007-10-09
what are some good java open source fps games? a lot of open source fps's that i see are in c/c++. i want to know the logic behind them, and maybe learn something new from java.  or maybe even use it as an engine

---

### Post by Juco on 2007-10-10
bump

---

### Post by shynko on 2007-10-10
I don't know of many. I found this simple one that you play in your browser. [http://www.pulpgames.net/scared/](http://www.pulpgames.net/scared/)

also there is Jake a quake 2 port to java

---

### Post by Darkagentx on 2007-10-10
> **shynko said:**
> I don't know of many. I found this simple one that you play in your browser. [http://www.pulpgames.net/scared/](http://www.pulpgames.net/scared/)

Pretty nifty, but tricky being used to playing them with a slightly different configuration.

---

### Post by Vadi on 2007-10-10
FreeCol is in java, I think.

---

### Post by Cpl Headshot on 2007-10-10
It's not an FPS, but [TripleA]("http://triplea.sourceforge.net/mywiki") is a fun strategy game. It's based on the board game Axis and Allies. [Here's]("http://tripleadev.org/index.php?") a good site for scenarios.

---

### Post by Juco on 2007-10-10
jake2 is great, and is exactly like what i am looking for. im going to look into the code, and see if i can play around with it.  is there anything else like it, a java open source fps?

---

### Post by Tomosaur on 2007-10-11
Hmm well, Java isn't all that great for making FPS games (FPS games tend to be speed critical, so developers naturally favour C/C++ over Java to write such games).

If all you want to do is look at the source code anyway, then why not just pick any of the existing open-source FPSs? Java is a C-like language, although C isn't object oriented. C++ is more similar to Java - you'd only need to 're-learn' a few things, which would take you all of half an hour really. The biggest problem is learning the various libraries at your disposal, but there's enough documentation freely available on the net for you to be able to find what you need to know relatively easily.

As an aside, many modern FPS games tend to use OpenGL - so you will also need the JOGL package: [https://jogl.dev.java.net/](https://jogl.dev.java.net/)

OpenGL is a challenge in itself, so be prepared for some reading!

Good luck :)

---

### Post by Asraniel on 2007-10-11
there is a open source quake 2 java engine. use google to find it, seems very good (same speed as native c code quake 2)

---

### Post by samjh on 2007-10-11
Not FPS specifically, but here are quite a few 3D Java games that use the JMonkey Engine:

[http://www.jmonkeyengine.com/index.php?option=com_content&task=view&id=68&Itemid=84](http://www.jmonkeyengine.com/index.php?option=com_content&task=view&id=68&Itemid=84)

Most of them are commercial independent developers (some big name ones too).

If you ask around in their forums, you'll probably get some good answers.

---

### Post by gouessej on 2010-11-16
Hi!

> **Tomosaur said:**
> Hmm well, Java isn't all that great for making FPS games (FPS games tend to be speed critical, so developers naturally favour C/C++ over Java to write such games).
It's wrong, it is only a prejudice. Java has been used in some commercial video games since 1995. Jake2, Undead Arena, Tesseract, Night Squad 2, Resistance Force, Scared, Future Arenas... are Java-based FPS.

My own FPS is not wonderful but free and open source:
[http://tuer.sourceforge.net](http://tuer.sourceforge.net)

It uses JOGL. The next version uses Ardor3D and allows to use 2 guns at the same time :)

---

### Post by gouessej on 2011-02-23
Hi!

Sorry to revive such an old thread.

> **Tomosaur said:**
> Hmm well, Java isn't all that great for making FPS games (FPS games tend to be speed critical, so developers naturally favour C/C++ over Java to write such games).

This sentence was already stupid 4 years ago, it is even more silly now. Java has a lot of First Person Shooters including (most of them are open source): 
- [Scared]("http://www.pulpgames.net/scared/")
- [Undead Arena]("http://home.halden.net/tombr/squareheads/squareheads.html")
- [Wolkenstein]("http://jmonkeyengine.org/groups/free-announcements/forum/topic/wolkenstein-fps-ready/?topic_page=2")
- [JavaIsDoomed]("http://javaisdoomed.sourceforge.net/")
- [Jake 2]("http://bytonic.de/html/jake2.html")
- [Resistance Force]("http://www.resistanceforce.com/")
- [Night Squad 2]("http://nightsquad2.freenet.de/nightsquad2/?lan=en")
- Futuristic Arenas
- Ancient Arenas
- [Flesh Snatcher]("http://sourceforge.net/projects/fleshsnatcher/")
- [Tesseract]("http://tesseract-fps.sourceforge.net/")
- [T.U.E.R (+ JFPSM)]("http://tuer.sourceforge.net")

Long life to Java, JOGL and free open source softwares.

---

