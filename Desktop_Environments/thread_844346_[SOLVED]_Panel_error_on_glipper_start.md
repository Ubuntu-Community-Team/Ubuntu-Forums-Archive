---
title: "[SOLVED] Panel error on glipper start"
date: 2008-06-29
forum: Desktop Environments
---

### Post by vlc on 2008-06-29
Hi *,

I added the glipper clipboard manager to the gnome panel and now I get sometimes after gnome start the following error message:

[FONT="Courier New"]**The panel encountered a problem while loading "OAFIID:Glipper".**[/FONT]

Then I have to add the glipper manually to the panel.

Does anyone have an idea what could cause this error?

Thank you very much in advance!

---

### Post by cpetercarter on 2008-06-29
No idea - I have the problem too, but I find that if I just click on the error message box, Glipper installs anyway.

---

### Post by kbuel on 2008-06-30
I'm getting this error also.  Is there a place where these errors would be logged that we could look at it?

---

### Post by vlc on 2008-06-30
I think I found a workaround in the [launchpad]("https://bugs.launchpad.net/ubuntu/hardy/+source/glipper/+bug/213494"):

> I have a temporary fix for this problem. The fact that it happens sometimes led me to believe that apparently there is some daemon or environment that has not been started yet at the moment that Glipper loads (so, Glipper is "too fast" with starting). So I added a wait period in the starting of Glipper, and that fixed the problem. The time-out is in itself not a problem, I don't mind that Glipper starts for instance half a minute later, as long as I do not have to re-add it every time I boot my laptop.

So what to do: Look up Glipper and add a wait statement:

sudo gedit /usr/lib/glipper/glipper

Make sure the code in the beginning looks like this:

#!/usr/bin/env python

# Glipper - Clipboardmanager for GNOME
# Copyright (C) 2007 Glipper Team
# bla bla bla
# License along with this library; if not, write to the
# Free Software Foundation, Inc., 59 Temple Place - Suite 330,
# Boston, MA 02111-1307, USA.
#

import time # <-- This line is new
time.sleep(8) # <-- This line is new. Change the 8 to for instance 30 if it did not help

import gobject
gobject.threads_init()

import gtk, gnomeapplet, gnome
import getopt, sys
from os.path import *


It seems to be working for me.

---

