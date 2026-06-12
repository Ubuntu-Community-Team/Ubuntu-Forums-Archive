---
title: "Trouble with mame"
date: 2008-03-17
forum: Gaming &amp; Leisure
---

### Post by liquidjellos on 2008-03-17
Hello all,

I"m rather new to ubuntu and having some trouble with mame. I tried searching for my solution, but I couldn't find a thread that accurately solved my problems, so here goes.

i've got kxmame up and running for the most part, the executable is working, and it found the entire game list without a problem. I downloaded a rom and left it zipped like the how-to's say to do, and after I navigate to the directory where they are "usr/games/" and select them, i get an error message stating "/usr/games/mslugx.zip is not a valid xmame executable".

I thought you were supposed to leave them as zip files, so what gives? any help is appreciated.

Thanks!

---

### Post by DoktorSeven on 2008-03-17
kxmame is simply the front-end to the xmame (or newer SDLmame); you need to download xmame itself and point kxmame to it.

In Settings->Directories->KXMame paths, you should navigate to /usr/games/xmame (or sdlmame, or xmame.SDL, or whatever you have installed).

Then on Mame/Mess basic paths, navigate to where you have the ROMs installed.  (If you're using SDLmame and the SVN version of kxmame for use with SDLmame, you'll actually set that in /etc/sdlmame/mame.ini).

You'll then select the ROM in the Available list in the main GUI.

Finally, note that Metal Slug X also requires the Neo-Geo BIOS to be in the same ROM directory you set (where mslugx.zip is as well), just like all NeoGeo games.

Try [checking out this thread](http://ubuntuforums.org/showthread.php?t=545066) for more details setting up a new (SDLmame) version of MAME using wahcade, or scroll down in the thread to a link to a newer version of SDLmame that works with it.

---

