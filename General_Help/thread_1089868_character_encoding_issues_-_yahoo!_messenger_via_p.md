---
title: "character encoding issues - yahoo! messenger via pidgin/web"
date: 2009-03-07
forum: General Help
---

### Post by instantkarma on 2009-03-07
I already posted this issue at: [http://ubuntuforums.org/showthread.php?t=1087804]("http://ubuntuforums.org/showthread.php?t=1087804"), but no one's responded at all so I figured I'd move it here.

Basically, pidgin and yahoo! web messenger print out hebrew output in jibberish like this:

[[IMG]http://img5.imageshack.us/img5/8034/pidgin.jpg[/IMG]](http://img5.imageshack.us/my.php?image=pidgin.jpg)

Can someone can please help or at least give a direction?

---

### Post by saffsd on 2009-03-07
I don't have a full solution for you, but I can tell you you have a problem with character encodings. I don't know how much you know about the topic, so here is wikipedia as a primer:

[http://en.wikipedia.org/wiki/Character_encoding](http://en.wikipedia.org/wiki/Character_encoding)

The character encoding used is controlled by your locale, have a look under 

System -> Administration -> Language Support

See if you have Hebrew enabled there, and if not, see if enabling it helps.

---

