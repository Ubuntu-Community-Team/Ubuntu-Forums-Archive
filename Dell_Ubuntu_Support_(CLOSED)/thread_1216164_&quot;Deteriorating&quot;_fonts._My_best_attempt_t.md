---
title: "&quot;Deteriorating&quot; fonts. My best attempt to fix it messed even more"
date: 2009-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by the dsc on 2009-07-18
I've installed ubuntu 9.04 (server, initially, but now has ubuntu-desktop and xubuntu-desktop) on a Latitude X 200, it works almost fine, but there was a tendency to the graphics, apparently mostly text, to "deteriorate", the characters would start to appear somewhat deformed in one way or another, somewhat "bold", fusing with adjacent characters, and with some random tiny lines on them. Title bars colors also look somewhat "messy", with blocks on wrong colors, specially with XFCE.

I've tried to fix it first by installing xubuntu, but was not different, but I hadn't much hope on that anyway.

Then I thought that could be a xorg.conf thing, since in the same computer, running Knoppix, didn't have these issues. So, I've just copied Knoppix generated xorg to ubuntu (which surprisingly was blank).

Then occurred something I couldn't expect. Instead of just not working, or not fixing it, now when X is to start, the screen just remains dark for a little while, then starts to brigthen and become somewhat greenish, reminding a bit those "visualisations" of audio files on audio players like Kaffeine. 

First the "single" mode was buggy, but now I could at least remove Knoppix' xorg.conf with it, and everything is back to "normal".


Knoppix' xorg is 1.7.0-8, while Ubuntu's is somewhat newer. 


My best guess would be to downgrade to some ubuntu with that xorg version, as a extreme measure, or at least downgrade just xorg, if by doing that will not result in any dependency conflict with current packages. Hoping that Ubuntu's and Knoppix' are similar enough so that having the one that work with the former will fix it.


Anyone has a better idea? Thanks in advance.

---

### Post by the dsc on 2009-07-20
Solved, so to speak. I've installed ***K***ubuntu 8.04-2, and no sign of the deteriorating fonts. It may be a different version of the xorg's driver for Dell's video, or maybe someting related with kwin versus metacity, or whatever is that handles the windows these days. I tried both at the same time to increase the odds.

I'll still have to install at least network-manager from gnome if I want the wireless to work easily. KDE's stuff just ignores it. I hope it won't force much of gnome, specially the part that was having trouble with the video board.

:-/

---

