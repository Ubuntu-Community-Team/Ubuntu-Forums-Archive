---
title: "sdlmame vs Gnome Video Arcade"
date: 2008-05-23
forum: Gaming &amp; Leisure
---

### Post by Dan_Dranath999 on 2008-05-23
I installed SdlMame, and it works fine. (Changed the path to the roms in the .ini file, to a folder in my home directory) It finds the roms, and plays them.

Compiled Gnome Video Arcade, but it fails to build the game list (it says there isn't any roms)

---

### Post by Dan_Dranath999 on 2008-05-23
Funny thing: if i write ```
gnome-video-arcade --inspect rompath
``` in the terminal, it should return the path i inserted earlier in the sdlmame.ini, and it does in fact.

So, i don't know why sdlmame plays the roms but Gnome-Video-Arcade won't!

---

### Post by DoktorSeven on 2008-05-23
Seems that Gnome Video Arcade is buggy.  I compiled it myself and got the same result, plus it crashed on me a couple of times.

kxmame is a better overall frontend to use (even though it relies on KDE stuff); you'll need the SVN version to use with sdlmame though.  I have a package [here](http://sdcofer.googlepages.com/) to try.

---

### Post by disturbedite on 2008-05-23
yeah, definitely take DoktorSeven's advice.  it is the best way to go imho.

---

### Post by Dan_Dranath999 on 2008-05-23
what about QMC2 (mamecat2)?  Looks interesting, but it might be harder to compile for gutsy -need to compile qt4 first (the Qt 4.3.2 version in the repositories is supossed to be buggy)

---

### Post by disturbedite on 2008-05-24
> **Dan_Dranath999 said:**
> what about QMC2 (mamecat2)?  Looks interesting, but it might be harder to compile for gutsy -need to compile qt4 first (the Qt 4.3.2 version in the repositories is supossed to be buggy)
we have qt 4.4 in intrepid.

---

### Post by Dan_Dranath999 on 2008-05-26
> **disturbedite said:**
> we have qt 4.4 in intrepid.

intrepid? (i was thinking about compile the latest QT, but got lazy)

Anyway, gave up on Gnome-Video-Arcade, and tried XMamegui (java) and it works. But when choosing a game, you have to wait 15 or 20 seconds until the mouseclick takes effect (and meanwhile, the whole program ends up frozen)    

Then, Loemu...   from a Deb package. And it just won't build the game list. (when i get home i'll post the error messages from the terminal)

---

### Post by disturbedite on 2008-05-26
> **Dan_Dranath999 said:**
> intrepid? ...
[URL="https://wiki.ubuntu.com/IntrepidIbex"]intrepid ibex
[/URL]

---

### Post by Dan_Dranath999 on 2008-05-26
This happens when  Loemu calls for the game list:

```
daniel@CajaBase:~$ loemu
Unhandled exception in thread started by <bound method MainWindow.load_process of MainWindow(path="/usr/share/loemu/glade/Loemu.glade", root="main_window")>
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/loemu/Loemu.py", line 521, in load_process
    err = self.gamelist.load()
  File "/usr/lib/python2.5/site-packages/loemu/Gamelist.py", line 134, in load
    err= self.load_list()
  File "/usr/lib/python2.5/site-packages/loemu/Gamelist.py", line 102, in load_list
    saxparser.parse(open(file))
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 109, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/xmlreader.py", line 125, in parse
    self.close()
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 226, in close
    self.feed("", isFinal = 1)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 220, in feed
    self._err_handler.fatalError(exc)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: /home/daniel/.loemu/gamelist.xml:23:0: no element found
```


Some Python error?

---

### Post by elamericano on 2008-05-26
From: Mamecat FAQ:

    * Ubuntu 7.10 (Gutsy Gibbon) comes with Qt 4.3.2, which is buggy. Please see Q3.2!
    * Ubuntu 8.04 (Hardy Heron) comes with Qt 4.3.4, which is perfect!

Did someone seriously suggest Intrepid to solve this issue?! Yeah, like that wouldn't cause any problems.

---

### Post by elamericano on 2008-05-26
I just built the current svn version using the instructions here:

[http://qmc2.svn.sourceforge.net/viewvc/*checkout*/qmc2/data/doc/html/us/faq.html#A1.7.1](http://qmc2.svn.sourceforge.net/viewvc/*checkout*/qmc2/data/doc/html/us/faq.html#A1.7.1)

The current stable release does *not* build on Ubuntu, use svn instead.

---

