---
title: "PSX Losing Sound After Upgrade"
date: 2010-10-12
forum: Gaming &amp; Leisure
---

### Post by gerowen on 2010-10-12
I've been using the Windows version of PSX with wine now for a while to play my old Playstation games because I use 64 bit Ubuntu, and the Linux version of PSX looks for really old versions of a bunch of 32 bit libraries.  Well after upgrading to 10.10, I noticed that when you start up PSX, you have sound, but once you use the menus to load a game, you lose all sound unless you go into the sound menu, set the device to "Disabled", apply, close, then open it back up and turn it back on.  To avoid this I wrote a small python script (see text below) that I dropped in the folder with the PSX executable that just launches PSX with the image pre-loaded, but I was wondering if anybody else noticed this and has a way to fix the issue other than just my little workaround.  Note, the reason I don't automatically insert quotes is because if you drag and drop an image file into the terminal window of the python script, it automatically inserts quotes for you.

```

import os
print ""
game=raw_input("Enter the full path with quotes to the CD image: ")
os.system(("wine psxfin.exe %s")%(game))

```

---

