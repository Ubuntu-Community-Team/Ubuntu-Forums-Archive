---
title: "Need Help with using Proton on Steam (Idle Champions of the Forgotten Realms)"
date: 2020-01-14
forum: Gaming &amp; Leisure
---

### Post by muscl3s on 2020-01-14
I'm running ubuntu 19.10 on a new Dell laptop.  Specs are:

15.6" 1080P Anti-Glare IPS Display
AMD Ryzen 7 3700U 2.3 GHz (4 GHz Turbo, 6MB Cache)
AMD VEGA 10 Graphics
16GB (4GBx2) DDR4 2333 MHz Ram 
256GB M.2 PCIe NVMe SSD

I'm completely new to Linux but I got everything running okay including Steam.  However, I'm having a difficult time trying to get my first game running using Proton.  According to the Proton site, the game runs flawless:
[https://www.protondb.com/app/627690](https://www.protondb.com/app/627690)

Nothing seems to happen when attempting to launch the game from Steam.  What steps do I need to take to get this running?

---

### Post by mastablasta on 2020-01-15
you need to install it using proton. if it's a steam game you need to enable steam play.

[https://linuxconfig.org/how-to-install-and-use-steam-play-on-linux](https://linuxconfig.org/how-to-install-and-use-steam-play-on-linux)

---

### Post by oldrocker99 on 2020-01-15
Right-click the file in your library, then select Properties. Paste this into the Launch Options:
```
PROTON_USE_WINED3D=1 %command%
```
This works for a raft of games.

This does assume that you **have** enabled Steam Play. Go to Steam/Settings. Open the Steam Play tab and click "Enable Steam Play for supported titles," AND "Enable Steam Play for all other titles." You'll have to exit and restart Steam, and, using that start option, a very large number of Windows games are playable.

DO check [https://www.protondb.com](https://www.protondb.com) to see *if* the game will run, or *how* the user got the game running, or if the game simply is borked and you should avoid the hassle of purchasing, then having to refund it.

I have the same game installed, and, with that start option, it runs perfectly.

---

### Post by muscl3s on 2020-01-15
I already had Steam Play installed and everything running normally but the game would not launch after installing.  Nothing would appear on the screen either.  A friend recommended I just install Pop OS and I didn't have any problems running the game right away.  Clearly something was missing in the Ubuntu install preventing me from getting it to work.

---

