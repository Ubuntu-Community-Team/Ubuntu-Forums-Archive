---
title: "GNUChess removes Gnome-Games"
date: 2007-05-19
forum: Gaming &amp; Leisure
---

### Post by Ian Christie on 2007-05-19
Can anyone explain why, in Fiesty, when I install GNUChess, Synaptic wants to uninstall gnome-games? I know gnome-games comes with a chess game, human vs computer says the computer is GNUchess, however, I have Gcompris installed for my 6yr old and the chess game in it requires GNUChess and won't work.

So basically I can't use the chess game in gcompris without losing all the other games that were installed originally.

---

### Post by DoktorSeven on 2007-05-19
Apparently, for some crazy reason they have gnuchess listed as a conflict with gnome-games; the only bug I found that attempts to explain this is [this one](https://bugs.launchpad.net/ubuntu/+source/gnuchess/+bug/80791) (last post).

Only thing I can think of is to install gnuchess from source so it won't mess up the dependencies.  Source is [here](http://mirrors.kernel.org/gnu/chess/).

---

### Post by Ian Christie on 2007-05-19
thanks for the response. I'll try that

---

