---
title: "gpodder - doesn't run"
date: 2006-11-20
forum: Desktop Environments
---

### Post by urusaiyatsu on 2006-11-20
Hello,

Just tried running gpodder again after a month or so and get the following:

~$ gpodder
Traceback (most recent call last):
  File "/usr/bin/gpodder", line 141, in ?
    sys.exit(main())
  File "/usr/bin/gpodder", line 137, in main
    gpodder.main( __version__)
  File "/usr/lib/python2.4/site-packages/gpodder/gpodder.py", line 1227, in main
    g_podder = Gpodder()
  File "/usr/lib/python2.4/site-packages/gpodder/gpodder.py", line 109, in __init__
    SimpleGladeApp.__init__(self, path, root, domain, **kwargs)
  File "/usr/lib/python2.4/site-packages/gpodder/SimpleGladeApp.py", line 108, in __init__
    self.new()
  File "/usr/lib/python2.4/site-packages/gpodder/gpodder.py", line 180, in new
    self.channels = reader.read( False)
  File "/usr/lib/python2.4/site-packages/gpodder/libgpodder.py", line 338, in read
    parser.parse( gPodderLib().getChannelsFilename())
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/expatreader.py", line 109, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/xmlreader.py", line 123, in parse
    self.feed(buffer)
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/expatreader.py", line 220, in feed
    self._err_handler.fatalError(exc)
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: /home/paul/.config/gpodder/channels.xml:24:84: not well-formed (invalid token)

I've tried uninstalling and re-installing from Synaptic and the .deb version but all no good.

Can someone give me an idea what's going on here? I'm using Edgy.

Thanks.

---

### Post by urusaiyatsu on 2006-11-20
bump. anyone?

---

### Post by philidox on 2007-11-15
Perhaps upgrading to gutsy?

---

