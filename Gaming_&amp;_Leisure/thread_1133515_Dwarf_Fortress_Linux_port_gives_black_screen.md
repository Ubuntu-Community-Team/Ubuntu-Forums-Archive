---
title: "Dwarf Fortress Linux port gives black screen"
date: 2009-04-23
forum: Gaming &amp; Leisure
---

### Post by Inquisitorthemad on 2009-04-23
I have downloaded and installed the Linux port of Dwarf Fortress for my machine, and got all the dependencies I thought it needed. However, when I start it up, it shows colours for a few moments before the window turns black.

This cannot simply be a game crash issue, as the music still plays at full speed, and if I change from fullscreen to windowed I get a brief flash of what the screen should be showing before it goes black again. Although technically the program's working, this does render it unplayable.

Does anyone know what could be causing this?

---

### Post by kenji_03 on 2009-08-10
Are you using the Linux native version or the Wine version?  The Dwarfwiki needs to be updated as it isn't very helpful (imho)

[http://www.bay12games.com/dwarves/df_28_181_40d13_linux.tar.bz2](http://www.bay12games.com/dwarves/df_28_181_40d13_linux.tar.bz2)

Download that one and run it not from the exe but the "df" file that has no extension.  It's a script file and it'll run the game if you click "Run in Terminal" (you don't have to run it yourself)

This native version does not require WINE so you avoid all those problems.  I have yet to see if I get any enhanced performance out of the Linux Native version, but keep in mind there ARE some bugs.  Every now and again your keyboard will stop responding.  Don't panic, just click off screen (or press F11 and _wait_ if you are in full screen mode, THEN click off screen).

Also, if you have an intel in your rig you might want to download the ia32-libs package.  I have been digging through the repository and cannot find it, but you can download and install it old-school from here: [http://packages.ubuntu.com/intrepid/i386/libsdl-image1.2/download](http://packages.ubuntu.com/intrepid/i386/libsdl-image1.2/download)

I hope this helped!

---

