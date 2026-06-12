---
title: "Problems with PySol"
date: 2007-03-04
forum: Gaming &amp; Leisure
---

### Post by ironfistchamp on 2007-03-04
Hey everyone

I am trying to install PySol on Feisty from the repos. It installs and all that (needed to get Python2.4 aswell) and now when I try to run it I get the error

```

Traceback (most recent call last):
  File "/usr/share/games/pysol/pysol.py", line 47, in ?
    from main import main
  File "/usr/share/games/pysol/main.py", line 54, in ?
    from app import Application
  File "/usr/share/games/pysol/app.py", line 54, in ?
    from images import Images, SubsampledImages
  File "/usr/share/games/pysol/images.py", line 47, in ?
    from pysoltk import tkversion, loadImage, copyImage, createImage
  File "/usr/share/games/pysol/pysoltk.py", line 81, in ?
    exec "from " + m + " import *"
  File "<string>", line 1, in ?
  File "/usr/share/games/pysol/tk/toolbar.py", line 46, in ?
    from actions import PysolToolbarActions
  File "/usr/share/games/pysol/actions.py", line 45, in ?
    from random import constructRandom
ImportError: cannot import name constructRandom

```

Can anyone help me figure out how to fix this. I do a little Python programming but I woudln't know how to fix this. 

Anyone got any ideas?

Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2007-03-04
Ok found out that PySol has it's own random module (poor name choice, should really be unique). Feisty/Python is loading the default one that is installed with Python. 

If you want this to work you need to rename the PySol random module to something like randomSOL. Then edit actions.py, app.py and game.py, changing random to randomSOL where necessary. 

Ironfistchamp

---

### Post by wilko on 2007-03-10
Followed your fix for this on Feisty - wife's favorite card suite.  Changed the random module to randomSOL and edited the 3 files replacing all instances of random (lowercase) with randomSOL but get the attached error.

Hope you can throw some light on this - always good to keep in with wife.

Thanks in anticipation.

---

### Post by ironfistchamp on 2007-03-10
That sounds a little odd. I am not sure what I can do to help other than package my fixed version up or post the imports bit from my three files. I'll post the code first and if that doesn't help you find the problem I will package up my changed files and you can just copy them over your current ones.


actions.py
```

# imports
import os, re, sys, string, time, types

# PySol imports
from mfxtools import *
from mfxutil import EnvError, SubclassResponsibility
from mfxutil import Struct, destruct, openURL
from util import PACKAGE, PACKAGE_URL, VERSION, bundle
from randomSOL import constructRandom

# stats imports
from stats import Status_StatsDialog, PysolStatsFormatter
from pysoltk import SingleGame_StatsDialog, AllGames_StatsDialog
from pysoltk import FullLog_StatsDialog, SessionLog_StatsDialog

# toolkit imports
from pysoltk import EVENT_HANDLED, EVENT_PROPAGATE
from pysoltk import MfxDialog, MfxSimpleSlider, MfxSimpleEntry
from pysoltk import MfxExceptionDialog
from pysoltk import MfxCheckMenuItem, MfxRadioMenuItem
from pysoltk import getFont
from pysoltk import PlayerOptionsDialog
from pysoltk import SoundOptionsDialog
from pysoltk import DemoOptionsDialog, HintOptionsDialog
from pysoltk import EditTextDialog
from help import helpAbout, helpAboutSimple, helpHTML

```


app.py
```

# imports
import sys, os, re, string, time, types
import traceback

# PySol imports
from mfxtools import *
from mfxutil import destruct, dumpmem, Struct
from mfxutil import pickle, unpickle, Unpickler, UnpicklingError
from mfxutil import merge_dict, getusername, gethomedir, getprefdir, EnvError
from mfxutil import latin1_to_ascii
from util import DataLoader, Timer, bundle, cyclops
from util import PACKAGE, VERSION, VERSION_TUPLE, CARDSET
from util import IMAGE_EXTENSIONS
from resource import CSI, CardsetConfig, Cardset, CardsetManager
from resource import Tile, TileManager
from resource import Sample, SampleManager
from resource import Music, MusicManager
from images import Images, SubsampledImages
from randomSOL import LCRandom64
from game import Game
from gamedb import GI, GAME_DB, loadGame

# Toolkit imports
from pysoltk import tkname, tkversion, wm_withdraw, wm_set_icon, loadImage
from pysoltk import bind, unbind_destroy
from pysoltk import MfxDialog, MfxExceptionDialog
from pysoltk import TclError, MfxRoot, MfxCanvas, MfxScrolledCanvas
from pysoltk import PysolMenubar
from pysoltk import PysolProgressBar
from pysoltk import PysolToolbar
from pysoltk import PysolStatusbar
from pysoltk import SelectCardsetByTypeDialogWithPreview
from help import helpAbout

```

game.py
```

# imports
import math, os, re, string, sys, time, types
from cStringIO import StringIO
import traceback

# PySol imports
from mfxtools import *
from mfxutil import Pickler, Unpickler, UnpicklingError
from mfxutil import destruct, Struct, SubclassResponsibility
from mfxutil import merge_dict, UnpicklingError, uclock, usleep
from util import PACKAGE, VERSION, VERSION_TUPLE, get_version_tuple, Timer
from util import ACE, QUEEN, KING
from gamedb import GI
from resource import CSI
from randomSOL import PysolRandom, LCRandom64, LCRandom31, WHRandom
from pysoltk import EVENT_HANDLED, EVENT_PROPAGATE
from pysoltk import CURSOR_WATCH, ANCHOR_SW, ANCHOR_SE
from pysoltk import tkname, bind, after_idle, wm_map, getFont
from pysoltk import MfxDialog, MfxExceptionDialog
from pysoltk import MfxCanvasText, MfxCanvasImage
from pysoltk import MfxCanvasLine, MfxCanvasRectangle
from pysoltk import Card
from move import AMoveMove, AFlipMove, ATurnStackMove
from move import ANextRoundMove, ASaveSeedMove, AShuffleStackMove
from move import AUpdateStackMove
from hint import DefaultHint
from help import helpAbout

```

I think the problem may be that you changed ALL instances. It only need to be in the imports section at the top. I believe the word "random" is used in function names and that in the PySOL random module. This would change it so it tries to read functions that don't exist. If you reinstall it (uninstall first maybe?) and then change the import sections in the three files to look like mine. 

Hope this helps you get it fixed


Ironfistchamp

---

### Post by wilko on 2007-03-10
Mega thanks - brilliant and yes I had changed all instances.

What are the odds of having a Python programmer on the forums that also likes the Pysol card suite!

My wife's now a very happy bunny and also sends her thanks.

---

### Post by ironfistchamp on 2007-03-10
Haha glad it worked. I wouldn't so much call myself a Python programmer, more of an enthusiast. One with a knack for asking questions. I am sure the people in the programming section will agree with. :p 

The only real reason I found PySol was because a relative wanted to move to Linux but would not live without MS Spider Solitaire. In the end I just got it running through Wine. All you need to do is grab the .exe for XP and run it with the animations turned off. Works a treat with the Ubuntu Human msstyle.

Glad I could help. Keep enjoying Ubuntu

Ironfistchamp

---

### Post by Mateo on 2007-03-11
i want to fix this.  but I don't know how to change a "random module"  so how do I do that? thanks.

---

### Post by ironfistchamp on 2007-03-12
Hi Mateo

It is pretty easy to change it. If you have installed PySol though Synaptic or used Apt-Get it should be installed to /usr/share/game(s)/pysol. As a user who has the persmission to read and write to that location (generally root so you could sudo it I suppose), go to the location and rename the file random.py to randomSOL.py. Then open the three files I specified above and change the imports setion to look like mine. That should be all you need to do.

HTH

Ironfistchamp

---

### Post by Mateo on 2007-03-12
got it, thanks.

---

### Post by MichaelSM on 2007-05-28
Hi. Best Solitaire download on the Net.I'm a music freak and just LOVE the background tracks. Who did them and are there more? I think I just downloaded  the most recent from Synaptic a week or so ago. Please help.
Mike.:KS

---

