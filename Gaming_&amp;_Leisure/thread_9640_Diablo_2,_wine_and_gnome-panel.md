---
title: "Diablo 2, wine and gnome-panel"
date: 2004-12-30
forum: Gaming &amp; Leisure
---

### Post by MightyFlea on 2004-12-30
Hi folks,

I have a little trouble with Diablo (LoD 1.10) running under wine (from the official wine-hq ubuntu apt sources):

After installation (which was troublesome, but finally worked) I can start Diablo all right, and wine (with the default settings unchanged) goes into full screen mode.

There are two problems though:
[list]
[*]The gnome-panel bars on the top and bottom of the screen remain visible. I can hide them with appropriate buttons, so that only small specks in the corner of the screen remain. I can live with that; it is a little inconvenient though.
[*]The major problem: After starting and exiting Diablo for two or three times the gnome-panel crashes and uses up 100% of the CPU time. The X server itself continues to work; failing a logout item the only thing I can do is reset the X server, kill the rampant gnome-panel from a console window and then login via gdm again.
[/list]

Oh; I have an nvidia Geforce 2MX graphics card with the nvidia binary driver from restricted, and I use warty.

Has anybody had this behaviour as well / any pointers where I could start looking?

Cheers,

Michael

---

### Post by piedamaro on 2004-12-30
You have to put the window "on top" with metacity, or by modifing your wine config file.
Cedega doesn't have this issue. (but it could have other issues).

---

### Post by MightyFlea on 2005-01-04
I now have it working.. mostly.
I can put the wine window on top (above the panels) by pressing Alt-Space and choosing from the window menu.
(I did not find any place in metacity or the wine config file where such things can be set.)

When the gnome-panel dies (which it does after two or three times of starting Diablo with wine) I can kill it and it just gets restarted.

I can live with this now. It is inconvenient however; so if anyone can give me pointer where to look, especially about the panel crash, it would be appreciated.

(On my old system, Woody with gnome-2.2 backport and wine from Sep. 04 compiled from source both of these problems did not occur.)

---

### Post by piedamaro on 2005-01-07
It doesn't occur with cedega on warty for me.

---

### Post by jdodson on 2005-01-07
[QUOTE=MightyFlea]I now have it working.. mostly.
I can put the wine window on top (above the panels) by pressing Alt-Space and choosing from the window menu.
(I did not find any place in metacity or the wine config file where such things can be set.)

When the gnome-panel dies (which it does after two or three times of starting Diablo with wine) I can kill it and it just gets restarted.

I can live with this now. It is inconvenient however; so if anyone can give me pointer where to look, especially about the panel crash, it would be appreciated.

(On my old system, Woody with gnome-2.2 backport and wine from Sep. 04 compiled from source both of these problems did not occur.)[/QUOTE]

you could install fluxbox and play d2 from there.  fluxbox would dump all that gnome stuff that you dont need and run the game faster anyway.  or you could just start X windows with wine calling d2.

---

