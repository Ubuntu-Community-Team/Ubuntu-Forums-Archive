---
title: "pcsx - works great with the exception of..."
date: 2008-05-06
forum: Gaming &amp; Leisure
---

### Post by drunkmatador on 2008-05-06
I did an install of PCSX from repositories, onto my x64 with Hardy. It seems to be running FF7 just fine (very good news for me and my girlfriend, we have not played this game since we were kids!).. the only problem is that I can't figure out how to get back to the menu once I'm playing. 

Holding down the esc key, the program will quit.. but I need to go to menu so that I can save state, quite frequently actually. Also if there are any keyboard shortcuts, or a way to assign them, that would be helpful too.

I was working on getting pSX working but it seems to be impossible for a x64 machine so I'm just sticking with this.. it looks great! Just need to save state and I'll be fine.

---

### Post by acoustibop on 2008-05-07
See here for dfreer's excellent [thread on installing/running pSX on 64bit Ubuntu]("http://ubuntuforums.org/showthread.php?t=394097"), drunkmatador.

---

### Post by drunkmatador on 2008-05-08
I tried that emulator a few days ago and I remember it not working. Probably only messed with it for ten minutes or so though, I'll do some more tonight.

BUT.. either the memory card files or save state has to be compatable, because we're in a game of Final Fantasy 7 now and would hate to start over. We'll just play the whole thing with no menu using key-shortcuts if that's all that is possible. Does this program have any key to go back to menu?

---

### Post by drunkmatador on 2008-05-08
Got pSX working just fine now. It's better than pcsx in my opinion, because (obviously) I can still use the menu after booting up a game.

---

### Post by acoustibop on 2008-05-08
Save states are not portable between emulators, drunkmatador - often they're not even portable between different versions of the same emulators.  However, pretty much all Playstation emulators use the same raw format for memory card saves, so memory card files are portable beween emulators.

The file extension doesn't matter - you may have to type the file name in for some emulators like ePSXe (and, I think, PCSX) if the file doesn't have its native extension (.mcr for ePSXe), but then emulator will then use it.  pSX doesn't care what the extension is - t will recognise and use any Playstation emulator memory card file.

However, don't forget that the version of the game matters.  You can't use saves from a PAL version of a game in an NTSC version, for instance, although I believe it's not difficult to hack saves so they can be used in another version.

---

### Post by drunkmatador on 2008-05-08
Cool thanks. Sure enough I just pointed pSX to the memory card files from pcsx, and they booted up just fine. Glad to be playing FF7 again, I love this game so much! Take care.

---

