---
title: "snes9x-gtk question"
date: 2010-02-13
forum: Gaming &amp; Leisure
---

### Post by scared0o0rabbit on 2010-02-13
So I've got snes9x gtk port (version: 79) installed, and it works great except for 1 problem.  I can't get cheats working in it.  That is to say, when I go into the cheats menu I can input action replay and game genie codes, but they don't actually do anything (and the codes are known to be good).

Does anyone else have this problem?  Is there a solution to this?  Is there an option I'm missing somewhere?

I've been resorting to using scanmem to cheat when I want to, which does work... kind of, but isn't perfect.

---

### Post by DoktorSeven on 2010-02-14
I just tried one myself and it seemed to work fine (an "infinite health" cheat on Dracula X).

I don't know what you could be missing other than you might have to hard reset the game (via the menu) for it to work, or you might be putting in a code for a different version of a game (different country, revision, etc), or just not entering the right thing somehow.  

I hate to just report "it works for me", but it does.

---

### Post by Gasen on 2010-04-01
I have the same problem. Cheats were working, I had done a system update (not sure if it included snes9x updates.) and I had also moved my roms folder. When I load a game the cheats are still there, but they don't do anything.

Under preferences/files theres a game data option, I set it to custom folder: -to my new rom folder location but still nothing.

---

### Post by Krang the Brain on 2010-04-02
SNES9X was alright until I found **ZSNES**.

---

### Post by scared0o0rabbit on 2010-04-02
Zsnes was alright until I found snes9x-gtk (this comes from a long time zsnes user).

I've been using zsnes since the CLI versions of the 90's, and I used zsnesw for windows since it came out.  My only prior experiences with snes9x had been with the original xbox.  Despite that, I jumped ship to the snes9x-gtk release over on ubuntu because it seems like it ran a bit better and then there's the fact that you can't beat super mario rpg on zsnes.

---

### Post by Gasen on 2010-05-11
I managed to get some cheats working by going into the cheat screen, deactivating the cheat, exiting and re-entering the screen, then activating the cheat and resuming the game.

The thing is, the cheat will only work once and I'll have to go back into the cheat screen and re-do those steps again.

GTK port version: 79
Snes9x version: 1.52

---

### Post by scared0o0rabbit on 2011-05-30
So here we are just over a year later and I've revisited this problem (I hadn't looked at it since my last post in this thread).  It looks like the version in the official repositories is still the same version that has this issue, (there is information out there to be had about what was causing it), but there is a newer version out (1.53) that corrects this.  I've found a repository you can get it from, however I don't know anything about the person who created it.  Just wanted to pass along what I'd found.

[https://launchpad.net/~bearoso/+archive/ppa]("https://launchpad.net/~bearoso/+archive/ppa")

PS.  If you do update to this version, expect to have to remove all your saved cheats and re-enter them before any will work, that's what I had to do.

---

