---
title: "(XGL) settings don't exist or aren't saved"
date: 2006-07-21
forum: Desktop Environments
---

### Post by yippy on 2006-07-21
I just got the compiz stuff working on my desktop, but with one weird problem.  Most of the settings don't exist in gconf-editor, and none of the settings are saved when I change things in gset-compiz.  With what I guess are the default settings it seems to be working great.

Has anyone else seen this happen before?

---

### Post by yippy on 2006-07-24
I rebooted several times and nothing changed, but then I booted into Windows over the weekend to play a game.  When I booted back into linux this morning it didn't seem to detect my monitor capabilities and stuck me in 640x480@60 (I've read others had that problem after installing xgl/compiz).  I manually set the refresh ranges in xorg.conf and got my real resolutions back, and somehow in that process the compiz settings appeared in gconf-editor and gset-compiz started working.  Go figure.

Unfortunately the compiz themer still doesn't seem to do anything, but at least the settings that matter work.

---

