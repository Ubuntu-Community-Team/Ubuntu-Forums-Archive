---
title: "Am I stupid or what?! It happened AGAIN!"
date: 2005-12-11
forum: Gaming &amp; Leisure
---

### Post by UltraSonicSite on 2005-12-11
I posted another topic about how America's Army doesn't work cause I was messing around with the video settings.

Well, stupid 'ol me downloaded a game that seemed pretty descent, you get it from Synapic Package Manager.

It's called Freecraft.

Well, using my amazingly smart noggin I decided to start messing around with ITS video options. My amazing skills were placed upon an option which put the game at a resolution I KNOW my computer can't handle.

Hurray.

Now I get this when the game attempts to run:
```
ultrasonicsite@Ubuntu-Network:~$ freecraft
FreeCraft default config file loading ...
640
480
800
600
1024
768
1280
960
1600
1200
... ready!
FreeCraft V1.18, (c) 1998-2003 by The FreeCraft Project.
  written by Lutz Sammer, Fabrice Rossi, Vladi Shabanski, Patrice Fortier,
  Jon Gabrielson, Andreas Arens, Nehal Mistry, Jimmy Salmon and others.
        (http://FreeCraft.Org)
  SIOD Copyright by George J. Carrette.
  libmodplug Copyright by Kenton Varda & Olivier Lapique.
  VP3 codec Copyright by On2 Technologies Inc.
  SDL Copyright by Sam Lantinga.
Compile options CCL ZLIB BZ2LIB SDL SDL-AUDIO SDL-CD SOUND
Compile feature UNIT-ON-MAP NEW-FOW NEW-AI

FreeCraft may be copied only under the terms of the GNU General Public License
which may be found in the FreeCraft source kit.

DISCLAIMER:
This software is provided as-is.  The author(s) can not be held liable for any
damage that might arise from the use of this software.
Use it at your own risk.

**[color=red]Couldn't set 1600x1200x0 video mode: No video mode large enough for 1600x1200[/color]**

```

...How do I change these settings to 800x600..?

---

### Post by JimmyBEng on 2005-12-11
I have never used freecraft, but if the directory ~/.freecraft is there you could try deleting it to reset the config.  Just a guess, maybe you have tried that or maybe it won't work with freecraft.

---

### Post by jasay on 2005-12-11
JimmyBEng is right I think.  In fact, looking in ~/.freecraft, there is a file called preferences1.ccl that looks like this```
;;; -----------------------------------------
;;; $Id: ccl.c,v 1.89 2003/03/08 06:59:57 nehalmistry Exp $
(set-video-resolution! 640 480)
```  You could probably just edit/delete this one file without affecting your other settings which appear to be in preferences2.ccl.

---

