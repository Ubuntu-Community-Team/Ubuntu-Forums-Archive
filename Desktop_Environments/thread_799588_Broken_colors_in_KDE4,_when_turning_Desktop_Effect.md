---
title: "Broken colors in KDE4, when turning Desktop Effects OFF"
date: 2008-05-19
forum: Desktop Environments
---

### Post by pilat on 2008-05-19
Strange problem in my Kubuntu 8.04 KDE4 remix.

I wouldn't post it if that were in "Desktop Effects: ON" mode, since ATI cards are not known to work very good with Compositing.

However, the problem is here specifically when I turn Desktop effects OFF.

So, just for short summary:

1. From the very beginning: Desktop Effects: OFF; all the colors Ok;
2. Enabled Desktop Effects (not Compiz, but built-in Kwin's compositing): colors Ok, despite some problems with playing video/running GL apps (it's Ok for ATI drivers);

... BUT:
3. since now, every time I disable Desktop effects, some pictures got incorrect colors (probably inverted), such as:
- Wallpaper image;
- Icons (including Files/Folders, App Icons (in menu, in Task bar and in "System tray").
- Windows decorations - for some themes _only_ (e.g., like "Plastic"; Oxigen seems to use normal colors... though it's gray theme, basically %)

Everything else seems to be shown correctly. Including all Fonts/WIndows contents (even images inside browser(firefox) look correctly).


General sense, that the problem affects "bitmap canvases" inside KD4 apps, only. Especially Plasmoids.


Any ideas? (actually, tried to google this question up.. seems it's not as common..)

---

### Post by GeneralZod on 2008-05-19
A picture paints a thousand words (accurate words, too), so please always include screenshots of visual anomalies rather than verbal descriptions :)

---

### Post by pilat on 2008-05-20
Here attached.

Notes:

#1: you can notice there couple of non-standard plasmoids. The problem firstly discovered without them.

#2: When I open e.g. Dolphin (KDE4 application) - all icons are Ok there. So not "inside KDE 4 aps", but rather "inside Plasma only".

#3. I also have some custom bits in my xorg.conf, accordingly to the very first topic of this thread in Compiz forums (did not install Compiz itself, however, and using KWin's built-in compositing):

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by pilat on 2008-05-20
Here's the KDE 4 app (Dolphin), but with different windows decoration.

The part of this decoration is broken as well, despite inside the window itself all icons have right colors :roll:

---

### Post by GeneralZod on 2008-05-20
Aargh - I've definitely seen this happen before (pre-4.0, I think) but I can't remember what the cause was :/

---

### Post by pilat on 2008-05-20
Well, It's not annoying then using Grey-colored windows decorations, such as Oxigen (the only icons and wallpaper get inverted, in this case). Moreover, it might be funny a bit (Kubuntu's blue colors become brown just like in Ubuntu) ;-)

Will look forward for further official updates from Kubuntu.

Let leave this topic opened for other suggestions/reports on the same issue 

(btw, it's strange that I couldn't find similar reports, before posting this one... since I'm using all-repo's Kubuntu...)

---

### Post by pilat on 2008-07-27
Has just updated to KDE 4.1 RC 1..

And even made 'rm -r .kde4'..

The broken colors are still here, when I'm turning Desktop Effect Off. :(

---

### Post by hq197 on 2008-10-23
I'm getting  the same thing in Fedora 9. I prefer GNOME so it wouldn't really matter, only when I open Konqueror from inside GNOME, even webpages turn up with a brown layer. Incidentally, when logging in, there's a brief flash of the kind of checked blocks one sees inside GIMP when working with layers. And the blocks are grey and brown (same color as the strange icons). Even my nice blue fedora start button has a brown tint now. I figured it's a strange layer which i never inserted there. No train smash. I'm sure it will get sorted under fedora 10.

---

### Post by pilat on 2008-10-23
UPD: the problem has gone, after I installer Catalyst 8.9. (with the one in Hardy repository -- the problem was permanent).

---

### Post by manradjan on 2008-12-07
I also have this problem with Ubuntu intrepid with kubuntu-desktop installed. This is on an old iBook (PPC), so only the opensource ati drivers are available. I've had the same issue with OpenSuse. On my other systems (x86) I don't have the problem, but they have nvidia cards with proprietary drivers.

---

