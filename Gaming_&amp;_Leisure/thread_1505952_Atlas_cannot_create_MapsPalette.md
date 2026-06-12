---
title: "Atlas cannot create Maps/Palette"
date: 2010-06-09
forum: Gaming &amp; Leisure
---

### Post by asqn34 on 2010-06-09
Hello everybody,

I have FG2 installed (in a separate folder in my home directory) with the script found on FG website.

I know I need to create palette but when trying this CL from FG website, I got this error: 
christophe@christophe-desktop:~$ Atlas --size=512 --atlas=/home/christophe/.fltk/Atlas --fg-scenary=/home/christophe/FGscript/data/Scenary --fg-root=home/christophe/FGscript/data --enable-navaids, I get a "lovely" Atlas is not installed.

I have tried this as well:
christophe@christophe-desktop:~$ cd '/home/christophe/FGscript' 
christophe@christophe-desktop:~/FGscript$ sh run_atlas.sh
Palettes::load: error loading palette file '/home/christophe/FGscript/install/fgfs/fgdata/Atlas/Palettes/default.ap': failed to open file
Palettes::load: error loading palette file '/home/christophe/FGscript/install/fgfs/fgdata/Atlas/Palettes/home/christophe/FGscript/install/fgfs/fgdata/Atlas/Palettes/default.ap': failed to open file
./Atlas: Failed to read palette file '/home/christophe/FGscript/install/fgfs/fgdata/Atlas/Palettes/default.ap

On FG website it is badly explained, as well as Atlas website, and i cannot find answers on the web.

Many Thanks**[B]**[/B]**[B][B][B]**[/B][/B][/B]

---

### Post by asqn34 on 2010-06-10
Solved.
Thank to zakharov (moderator on FG French forum) and Taureau89_9 (user of FG French forum)

[http://fr.flightgear.tuxfamily.org/foru](http://fr.flightgear.tuxfamily.org/foru) ... hp?id=1183

I created symlink for the .ap file located in /home/christophe/FGscript/Atlas/src/data/Palettes TO /home/christophe/FGscript/install/fgfs/fgdata/Atlas/Palettes.

Then I copied/paste the fonts folder in /FGscript/Atlas/src/data/fonts to /FGscript/install/fgfs/fgdata/Atlas
Then used the command ./Map (from within the folder containing the luncher) with the correct path for the scenery, data and atlas.

---

