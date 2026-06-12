---
title: "Loemu fails to load Game list for SDLMAME"
date: 2008-05-27
forum: Gaming &amp; Leisure
---

### Post by Dan_Dranath999 on 2008-05-27
This happens when  Loemu calls for the game list: 
(SDLMAME works with my roms, as Xmamegui does too)

It's supossed to build the game list, but fails to load it later.:confused: 

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

---

### Post by Dan_Dranath999 on 2008-05-29
tuc tuc?

---

