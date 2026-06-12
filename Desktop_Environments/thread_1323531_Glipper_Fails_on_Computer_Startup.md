---
title: "Glipper Fails on Computer Startup"
date: 2009-11-11
forum: Desktop Environments
---

### Post by Spectre5 on 2009-11-11
I was having a problem after each reboot/shutdown where glipper (a clipboard manager) would fail to load each time I started the computer.  I would get a dialog asking if I wanted to delete glipper from the panel or leave it.  If I logged out and back in, then it would load just fine.  The solution for me has been from post #96 at the following bug report:
[https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/213494]("https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/213494")

> This fix:

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

Worked for me, I had it set to 30, and then started crashing it regularly at startup. I upped it to 90 seconds, and that is working now. I also went through a bunch of stuff in my startup and eliminated bunch of things that shouldn't have been starting anyway.

I'm just posting this in case it helps others (and so I can easily find it when this problem arises in the future!).

---

### Post by theOGRE on 2010-06-04
I know this is really old, but thanks for the help man. This worked fine for me. PEACE

---

