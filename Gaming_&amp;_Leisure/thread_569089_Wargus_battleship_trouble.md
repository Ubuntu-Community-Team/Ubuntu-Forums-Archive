---
title: "Wargus battleship trouble"
date: 2007-10-06
forum: Gaming &amp; Leisure
---

### Post by balornt on 2007-10-06
I have been using wargus with stratagus for a little while now and love it, but I couldn't remember this game so well and so I am doing the campaigns. However on the level with your first experience with battleships (human) after the battleship fires when it should do an explosion animation/sound the game crashes and I get this error.

Trigger not set, defining trigger
Thanks for playing Stratagus.

Someone help me out here, I have tried playing around with soundz.lua in the different wargus folders with no success. I rebuilt it to restore it's original settings now and still have the same problem. Any advice?

---

### Post by disturbedite on 2007-10-06
i have experience compiling this and fixing some issues with wargus/stargus.  lua seems to be a nice language cuz it seems to consist of pretty much text files, so fixing some "issues" were easy for me being that i am not a programmer.
but i don't have any idea how to fix your issue.

did you say you recompiled it?
what i would do is completely uninstall it (manually of course since there aren't any deb packages for it, afaict) and then recompile and reinstall it.

also make sure you're using the latest version.  (2.2.4)

---

### Post by n0.obAtroN on 2007-10-07
hmmm. That is very strange. I have never had the a problem like that before. Did you get an error message "Segmentation Fualt"? If not, it is most likely you dont have libogg or libvorbis installed.

---

### Post by disturbedite on 2007-10-08
but would it have compiled without libogg or libvorbis?

---

### Post by balornt on 2007-10-08
I have installed all the required and recommended libraries (compiled all of them myself to be sure). It is the crappiest debug message I have seen. If it is a problem with the lua scripts then I don't know where or what to fix (though I looked at soundz.lua without much success) Anyway I tried changing the lua files in the wargus folder and they didn't affect the game at all. Did I change the wrong one? ( I tried /wargus/scripsts/soundz.lua /wargus/data.wc2/scripts/soundz.lua and /wargus/data.wc2/scripts/scripts/soundz.lua and none would change the BG music)

---

### Post by balornt on 2007-10-08
btw this did happen after I tried recompiling; there is a segmentation fault

balornt@balornt-laptop:~/games/wargus$ stratagus -d data.wc2/
Stratagus default config file loading ...

... ready!

Stratagus V2.2.4, (c) 1998-2006 by The Stratagus Project.
  written by Lutz Sammer, Fabrice Rossi, Vladi Shabanski, Patrice Fortier,
Jon Gabrielson, Andreas Arens, Nehal Mistry, Jimmy Salmon, and others.
        ([http://stratagus.org](http://stratagus.org))
Compile options ZLIB BZ2LIB VORBIS MIKMOD 

Stratagus may be copied only under the terms of the GNU General Public License
which may be found in the Stratagus source kit.

DISCLAIMER:
This software is provided as-is.  The author(s) can not be held liable for any
damage that might arise from the use of this software.
Use it at your own risk.

Trigger not set, defining trigger
Segmentation fault (core dumped)

---

### Post by disturbedite on 2007-10-09
i think you're calling the data (data.wc2 {wargus}) for stratagus incorrectly.  try entering the *full path* to the data file and report back.
here is mine for example:
/usr/local/bin/stratagus -d /usr/local/bin/wargus/data.wc2

---

### Post by balornt on 2007-10-10
yeah, I tried the full path thing and it produced the same results.

---

### Post by disturbedite on 2007-10-10
i don't know what else to tell you then, mine works...

---

### Post by n0.obAtroN on 2007-10-11
try installing a pre-compiled Stratagus package. Core-Dumped is not a good thing to get.

---

