---
title: "Creating a Openbox Pipe Menu"
date: 2009-03-26
forum: Desktop Environments
---

### Post by Major_Kong on 2009-03-26
How can i use openbox-xdgmenu to create a pipemenu for the gnome menus ?

By using the command 'openbox-xdgmenu /etc/xdg/menus/applications.menu' i get a dump to the xdg menu format of the items and sub-menus in applications.menu. How can i use this output to create a pipemenu ?

Thanks,
MK

---

### Post by der_joachim on 2009-03-27
On the openbox site there's a [collection of pipe menus]("http://icculus.org/openbox/index.php/Openbox:Pipemenus"). There's even a gnome application menu.

---

### Post by Major_Kong on 2009-03-27
Already check them out, but i can't figure out how to make openbox-xdgmenu work with the openbox menus.

Of what i understand, it should be enough to create a pipe menu that executes openbox-xdgmenu... but it does not work...

---

### Post by der_joachim on 2009-03-27
Hmmm... Have you installed python and all? I do not have a working Ubuntu anymore, so I cannot try the script. It apparently needs a python library called boplib.py (sic). Have you installed it?

---

### Post by Major_Kong on 2009-03-27
> **der_joachim said:**
> Hmmm... Have you installed python and all? I do not have a working Ubuntu anymore, so I cannot try the script. It apparently needs a python library called boplib.py (sic). Have you installed it?

It works if i run it in the console.

---

### Post by Major_Kong on 2009-03-27
Hmmm... i found out the problem, openbox-xdgmenu doesn't check for illegal characters, such as "&". Example: in the original gnome menu, there's one named "something & something", by using the command you still get one labeled "something & something" which is a big no-no...

---

### Post by GujuLvr on 2009-03-30
> **Major_Kong said:**
> Hmmm... i found out the problem, openbox-xdgmenu doesn't check for illegal characters, such as "&". Example: in the original gnome menu, there's one named "something & something", by using the command you still get one labeled "something & something" which is a big no-no...

huh i m trying out samething, wat do u mean by this. something & somethign?

---

### Post by Major_Kong on 2009-03-31
> **GujuLvr said:**
> huh i m trying out samething, wat do u mean by this. something & somethign?

That was just an example. The openbox xml menu format doesn't seem to like "&" in the menu name, but openbox-xdgmenu translates, for example, a menu named "Sound & Video" directly into "Sound & Video", without acounting for it.

---

### Post by nlvivar on 2010-06-08
> **Major_Kong said:**
>  openbox-xdgmenu doesn't check for illegal characters, such as "&".

Has anyone found a workaround for this? I still cannot get this to work properly. Can anyone give me a step-by-step tutorial on how to make one of these pipe menus to work?

Thanks.

---

### Post by nlvivar on 2010-06-08
I think that I have finally figured out how to do this. I gave up on openbox-xdgmenu for the same reasons that have been said in this thread: the "Sound & Video" category doesn't parse well.

In any case, here's how to get a Python script generated pipemenu.

Go here: [http://openbox.org/wiki/Openbox:Pipemenus#XDG_Application_Menus](http://openbox.org/wiki/Openbox:Pipemenus#XDG_Application_Menus)
Download the "Gnome Menus" and "boplib.py" Python scripts. Keep them in the same directory as each other.

Then add
```
<menu execute="python <path>/bop_gmenu.py" id="gmenu" label="Applications"/>
```
to your menu.xml file either with a text editor or with obmenu.

Now this should work!

---

### Post by Brandon Williams on 2011-01-10
> **nlvivar said:**
> Has anyone found a workaround for this? I still cannot get this to work properly. Can anyone give me a step-by-step tutorial on how to make one of these pipe menus to work?

Thanks.

This thread is a little old, but since I couldn't find a thread with a solution ...

I the following script: ~/bin/openbox-xdgmenu ```
#!/bin/sh
exec /usr/bin/openbox-xdgmenu "$@" | sed 's/&/&amp;/g'
``` This does the necessary substitution to fix "Sound & Video" so that I get valid XML from openbox-xdgmenu. After that, the pipe menu generated from the openbox desktop click is identical to the lxde panel menu.

---

### Post by benjo316 on 2011-01-10
A little ugly, but here's a slightly more complicated script that I made with just python which reads .menu files:

```
#!/usr/bin/env python2
#-*- coding:utf-8 -*-

from xdg import *
from xml.sax.saxutils import escape

import sys
import os

pipemenu = ''

def printMenu(menu, root=False):
    # Recursively prints xdg menus
    entries = list(menu.getEntries())
    for i in entries:
        entry = str(i).split('.')
        if hasattr(menu.getMenu(str(i)), 'Name') is True:
            print('<menu id="obxdgpipe_%s" label="%s">' % (escape(str(i)), escape(menu.getMenu(str(i)).Name)))
            printMenu(menu.getMenu(str(i)))
        else:
            print('<item label="%s"><action name="Execute"><execute>%s</execute></action></item>' % (escape(entry[0]), escape(entry[0])))
    if root == False:
        print('</menu>\n')

menu = Menu.parse(os.path.abspath(sys.argv[1]))

print('<openbox_pipe_menu>')
printMenu(menu, root=True)
print('</openbox_pipe_menu>')
```

It assumes that the program name is the same as the .desktop's file name (minus the .desktop part, of course)--which is usually okay, but may fail in some cases--because I couldn't figure out how to get that with pyxdg...

Edit: To use, just save to a file (say, obmenupipe.py) and add this to your menu.rc file somewhere:
```
<menu id="obmenupipe" label="Apps" execute="/path/to/obmenupipe.py /path/to/menu-file.menu" />
```

---

### Post by Version Dependency on 2011-01-11
You guys looking for a complete dynamic menu for openbox should check out: [https://launchpad.net/obmenugen](https://launchpad.net/obmenugen)

It's nice...but be warned before installing that it will rewrite your existing menu.xml so make a backup.

---

### Post by benjo316 on 2011-01-11
> **Version Dependency said:**
> It's nice...but be warned before installing that it will rewrite your existing menu.xml so make a backup.

That's why I wrote my script; I don't like stuff clobbering my config. Thanks, though. ;-)

Edit: Actually, looks like someone did something about the same as what I did, but more complete (but it looks like it uses functionality not yet present in the version of pyxdg that I have, and it's for fluxbox[/pekwm?]). [linky]("http://code.google.com/p/fluxbox-xdg-menu/source/browse/#svn%2Ftrunk"). Anyway, time for bed...

---

### Post by Brandon Williams on 2011-01-11
openbox-xdgmenu is already a complete dynamic menu for openbox that does not clobber menu.xml, and it's found in the standard repos. It just has this one small problem of not correctly handling the '&' character.

There's also obm-xdg from the obmenu package, but openbox-xdgmenu does a better job.

---

