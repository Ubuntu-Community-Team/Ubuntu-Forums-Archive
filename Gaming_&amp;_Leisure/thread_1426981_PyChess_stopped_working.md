---
title: "PyChess stopped working"
date: 2010-03-10
forum: Gaming &amp; Leisure
---

### Post by PC_load_letter on 2010-03-10
I just played PyChess like a couple of days ago and it was fine, now I have this:
```
$ pychess 
/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py:368: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py:351: Warning: IA__g_object_newv: object class `GtkWindow' has no property named `climb_rate'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py:351: Warning: IA__g_object_newv: object class `GtkWindow' has no property named `digits'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py:351: Warning: g_param_spec_pool_lookup: assertion `param_name != NULL' failed
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py:351: Warning: IA__g_object_newv: object class `GtkWindow' has no property named `(null)'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py:351: Warning: g_value_transform: assertion `G_IS_VALUE (src_value)' failed
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py:351: Warning: unable to set property `can-focus' of type `gboolean' from value of type `(null)'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))

```

Any idea what's going on? How to fix it?

Thanks.

---

### Post by Noraphalem on 2010-03-11
Hm. Ok warnings are in general no problem. Is the game starting up and running or crashing?

The messages in the terminal would let me suggest some problems with pygtk.

---

### Post by PC_load_letter on 2010-03-11
It opens the window where I choose the chess engine...etc. But once I click on START it freezes.

---

### Post by Noraphalem on 2010-03-11
Have you updated gtk+ or pygtk?

---

### Post by PC_load_letter on 2010-03-11
Ok, so I installed 'yolk' a Python utility to list all the installed Python modules, here is the output of **$ yolk -l**

```
Brlapi          - 0.5.3        - active development (/usr/lib/pymodules/python2.6)
CDDB            - 1.4          - active development (/usr/lib/pymodules/python2.6)
Conch           - 8.2.0        - active 
CouchDB         - 0.6          - active development (/usr/lib/pymodules/python2.6)
GnuPGInterface  - 0.3.2        - active development (/usr/lib/pymodules/python2.6)
Numeric         - 24.2         - active 
PAM             - 0.4.2        - active 
PIL             - 1.1.6        - active 
Pyste           - 0.9.10       - active development (/usr/lib/pymodules/python2.6)
Python          - 2.6.4        - active development (/usr/lib/python2.6/lib-dynload)
ScientificPython - 2.8          - active 
Twisted Core    - 8.2.0        - active 
Twisted Lore    - 8.2.0        - active 
Twisted Mail    - 8.2.0        - active 
Twisted Names   - 8.2.0        - active 
Twisted News    - 8.2.0        - active 
Twisted Runner  - 8.2.0        - active 
Twisted Web     - 8.2.0        - active 
Twisted Words   - 8.2.0        - active 
Twisted         - @twversion@  - active 
UniConvertor    - 1.1.4        - active development (/usr/lib/pymodules/python2.6)
apturl          - 0.4.1ubuntu2 - active 
ccsm            - 0.8.2        - active 
command-not-found - 0.1          - active 
computer-janitor - 1.12         - active development (/usr/lib/pymodules/python2.6)
configglue      - 0.2dev       - active 
cups            - 1.0          - active development (/usr/lib/pymodules/python2.6)
fstab           - 1.4          - active development (/usr/lib/pymodules/python2.6)
gnome-app-install - 0.4.1ubuntu1 - active 
httplib2        - 0.4.0        - active development (/usr/lib/pymodules/python2.6)
human-theme     - 0.37         - active 
jockey          - 0.5.5        - active 
launchpadlib    - 1.5.1        - active 
lazr.restfulclient - 0.9.3        - active 
lazr.uri        - 1.0          - active 
louis           - 1.7.0        - active development (/usr/lib/pymodules/python2.6)
lxml            - 2.1.5        - active 
matplotlib      - 0.99.0       - active development (/usr/lib/pymodules/python2.6)
mutagen         - 1.15         - active 
numpy           - 1.3.0        - active 
nvidia-common   - 0.0.0        - active 
oauth           - 1.0a         - active 
onboard         - 0.92.0       - active 
papyon          - 0.4.3        - active development (/usr/lib/pymodules/python2.6)
protobuf        - 2.0.3        - active development (/usr/lib/pymodules/python2.6)
pyExcelerator   - 0.6.3a       - active 
pyOpenSSL       - 0.9          - active development (/usr/lib/pymodules/python2.6)
pychess         - 0.10beta1    - active 
pycrypto        - 2.0.1        - active 
pyenchant       - 1.5.3        - active development (/usr/lib/pymodules/python2.6)
pygame          - 1.8.1release - active 
pyinotify       - 0.8.6        - active development (/usr/lib/pymodules/python2.6)
pyparsing       - 1.5.2        - active development (/usr/lib/pymodules/python2.6)
pyserial        - 2.3          - active 
pysqlite        - 2.5.5        - active 
python-apt      - 0.7.13.2ubuntu4 - active 
python-dateutil - 1.4.1        - active development (/usr/lib/pymodules/python2.6)
python-debian   - 0.1.14ubuntu1 - active development (/usr/lib/pymodules/python2.6)
pytz            - 2009l        - active 
pyxdg           - 0.15         - active development (/usr/lib/pymodules/python2.6)
rdflib          - 2.4.0        - active development (/usr/lib/pymodules/python2.6)
reportlab       - 2.3          - active 
scipy           - 0.7.0        - active 
screen-resolution-extra - 0.0.0        - active 
setuptools      - 0.6c9        - active 
simple-ccsm     - 0.8.2        - active 
simplejson      - 2.0.9        - active development (/usr/lib/pymodules/python2.6)
smbc            - 1.0          - active development (/usr/lib/pymodules/python2.6)
speechd_config  - 0.0          - active 
speechd         - 0.3          - active 
system-service  - 0.1.6        - active 
telepathy-python - 0.15.11      - active 
ubuntuone-storage-protocol - 1.0.1        - active 
ufw             - 0.29-4ubuntu1 - active 
unattended-upgrades - 0.1          - active 
usb-creator     - 0.2.8        - active 
virtkey         - 0.01         - active 
wadllib         - 1.1.2        - active 
wsgiref         - 0.1.2        - active development (/usr/lib/python2.6)
wxPython-common - 2.8.10.1     - non-active 
wxPython-common - 2.8.10.1     - non-active 
wxPython-common - 2.8.10.1     - active 
wxPython-common - 2.8.10.1     - active 
wxPython        - 2.8.10.1     - non-active 
wxPython        - 2.8.10.1     - non-active 
wxPython        - 2.8.10.1     - active 
wxPython        - 2.8.10.1     - active 
xkit            - 0.0.0        - active 
yolk            - 0.4.1        - active development (/usr/local/lib/python2.6/dist-packages/yolk-0.4.1-py2.6.egg)
zope.interface  - 3.5.2        - active 
```

Problem is, I don't see any PyGtk packages installed!!!? How come? I'm sure it was?

---

### Post by PC_load_letter on 2010-03-12
PyGtk is called python-gtk2 in the repos, and I have it installed. I opened Synaptic, then reinstalled it but to no avail. The version I have installed is the same one in the repos, v2.16.0ubuntu1

So, now what?

---

### Post by PC_load_letter on 2010-03-17
Now the other chess program (glchess) stopped working as well, the gui doesn't even show up.
Here is what I get from the terminal: 
```
$ glchess 
Traceback (most recent call last):
  File "/usr/games/glchess", line 77, in <module>
    start_game()
  File "/usr/lib/pymodules/python2.6/glchess/glchess.py", line 5, in start_game
    app.start()
  File "/usr/lib/pymodules/python2.6/glchess/main.py", line 690, in start
    g = self.addLocalGame(gameName, whiteName, None, blackName, black)
  File "/usr/lib/pymodules/python2.6/glchess/main.py", line 510, in addLocalGame
    p = g.addAIPlayer(blackName, self.__aiProfiles[profile], level)
  File "/usr/lib/pymodules/python2.6/glchess/main.py", line 114, in addAIPlayer
    p = player.AIPlayer(self.application, name, profile, level, description)
  File "/usr/lib/pymodules/python2.6/glchess/player.py", line 80, in __init__
    ai.Player.__init__(self, name, profile, level)
  File "/usr/lib/pymodules/python2.6/glchess/ai.py", line 287, in __init__
    self.connection.startGame()
  File "/usr/lib/pymodules/python2.6/glchess/uci.py", line 82, in startGame
    self.__sendCommand('ucinewgame')
  File "/usr/lib/pymodules/python2.6/glchess/uci.py", line 72, in __sendCommand
    self.__queuedCommands.append(command)
AttributeError: 'NoneType' object has no attribute 'append'

sh: bug-buddy: not found

```

Now it seems like it's a Python issue except I can not figure out what the heck is going on.

---

### Post by urmomsgoat on 2010-09-19
It's a known issue. I see it happening often when I've changed something in the pychess code and the python interpreter has to re-bytecompile (or whatever you call it) the python source code. But it seems to only happen on the first attempt at starting pychess, and then starting it the second time around works fine. I have no idea why it happens but since it doesn't happen every time I haven't put priority on figuring out what's going on. If I had to guess I'd say it's some sort of glade file versioning mismatches.

If you have time, file a bug report at [http://code.google.com/p/pychess/issues/entry](http://code.google.com/p/pychess/issues/entry)

---

### Post by urmomsgoat on 2010-09-25
I didn't see your followup about it freezing when you try to start a game (in pychess). That sounds looks like what I described in [URL="http://code.google.com/p/pychess/issues/detail?id=337&q=crash#c54"]http://code.google.com/p/pychess/issues/detail?id=337&q=crash#c54
[/URL]
Try turning off "Assistive Technologies" if it's turned on by going to "System > Preferences > Assistive Technologies" and making sure the "Enable Assistive Technologies" checkbox is unchecked.

---

