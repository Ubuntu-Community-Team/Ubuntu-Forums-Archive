---
title: "Running game in Wine turns desktop black"
date: 2007-03-20
forum: Gaming &amp; Leisure
---

### Post by D-- on 2007-03-20
Hi, everything I use in Wine runs fine except one game: Hydlide. Whenever I run it, the entire desktop turns jet black except for the Wine window.

Exiting th egame will not make the desktop turn back to normal. Only areas where something has moved will become visible again, so I either have to maximize a window to full screen or wave a window all over the place to "uncover" my desktop again.

This is happening in Xfce. I have not tested if the same happens in GNOME. It only occurs with this one game. All my other games in Wine run fune.

See attached screenshot.

(Note: The game otherwise plays just fine. I have finished it in Wine.)

---

### Post by FuturePilot on 2007-03-20
Try disabling Beryl before running the game. Beryl doesn't go over too well with certain games, especially 3D ones.

---

### Post by Lystrodom on 2007-03-21
What? Isn't Hydlide a NES game?

---

### Post by hikaricore on 2007-03-21
Are you sure your game even works?

Not every windows game works in wine, especially direct3d games.  I saw alot of d3d calls in your terminal window.

I checked appdb.winehq.org, but there's no mention of your game there.

Perhaps you should search google to see if anyone mentions it running under linux.

---

### Post by D-- on 2007-03-26
1. I'm not running Beryl. I'm running Xfce4. The results are the same with or without compositing enabled.

2. Hydlide is a NES game. And an MSX game, Genesis Game, FM7 game, PC-88 game, DOS game, PC-Windows game, and several other platforms. This one is the PC Windows one I did an English translation for a few years ago.

3. Given I completed the game in Wine already, yes, I'm quite sure it runs in Wine! It's not in the Window database, but Wine runs lots of things not in the Wine database. I also beat it on Windows back when I did the translation for it, and there was no difference playing under Wine.

The only problem with the game is that it turns the desktop black on load. Waving the window around, or else maximizing another window then restoring it, will fix the desktop. Everything continues to run fine, and it never blackens the desktop again. It's just inconvenient, and so I hoped someone might have another idea on how to fix it.

---

