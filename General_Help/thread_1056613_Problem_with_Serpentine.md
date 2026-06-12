---
title: "Problem with Serpentine"
date: 2009-01-31
forum: General Help
---

### Post by Langsuyar on 2009-01-31
Hi,

I'm a newbie in Ubuntu and i was trying to launch serpentine and it just doesn't open.
Launching it from the terminal, i get this :

serpentine
Traceback (most recent call last):
  File "/usr/bin/serpentine", line 114, in <module>
    from serpentine.common import SerpentineError
  File "/usr/lib/python2.5/site-packages/serpentine/__init__.py", line 40, in <module>
    from serpentine.mastering import GtkMusicList, MusicListGateway
  File "/usr/lib/python2.5/site-packages/serpentine/mastering.py", line 39, in <module>
    from serpentine import xspf
  File "/usr/lib/python2.5/site-packages/serpentine/xspf.py", line 27, in <module>
    from serpentine.compatxml import parseUri, Evaluate
  File "/usr/lib/python2.5/site-packages/serpentine/compatxml.py", line 5, in <module>
    from Ft.Xml.Domlette import NonvalidatingReader
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Domlette.py", line 29, in <module>
    from Ft.Xml import InputSource
  File "/usr/lib/python2.5/site-packages/Ft/Xml/InputSource.py", line 355, in <module>
    DefaultFactory = InputSourceFactory(catalog=GetDefaultCatalog())
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Catalog.py", line 579, in GetDefaultCatalog
    catalog = Catalog(uri, quiet)
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Catalog.py", line 95, in __init__
    self._parseXmlCat(data)
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Catalog.py", line 377, in _parseXmlCat
    p.parse(source)
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Catalog.py", line 476, in startElementNS
    delegate = Catalog(catalog, self.quiet)
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Catalog.py", line 95, in __init__
    self._parseXmlCat(data)
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Catalog.py", line 377, in _parseXmlCat
    p.parse(source)
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Catalog.py", line 476, in startElementNS
    delegate = Catalog(catalog, self.quiet)
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Catalog.py", line 95, in __init__
    self._parseXmlCat(data)
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Catalog.py", line 377, in _parseXmlCat
    p.parse(source)
xml.sax._exceptions.SAXParseException: file:///usr/share/xml/gnustep/gsdoc-1_0_0.dtd:41:0: syntax error


Any help is highly appreciated  :)

Lang

---

### Post by guine on 2010-07-31
Bump, I'm having this exact same problem.  Anyone have any ideas how to fix this?

---

