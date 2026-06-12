---
title: "Steam: steamoverlayrenderer.so cannot be preloaded, with Bumblebee"
date: 2014-10-11
forum: Gaming &amp; Leisure
---

### Post by zhongfu on 2014-10-11
Hello there! Recently, attempting to run Steam games with optirun/primusrun from the Steam client would result in a crash. For example, Team Fortress 2 would crash a few seconds after starting, and these would show in the terminal:
```
Game update: AppID 440 "Team Fortress 2", ProcID 28407, IP 0.0.0.0:0ERROR: ld.so: object '/home/zhongfu/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/zhongfu/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/zhongfu/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.


malloc: unknown:0: assertion botched
free: called with unallocated block argument
last command: (null)
Aborting...Game removed: AppID 440 "Team Fortress 2", ProcID 28407
```

Running the game from [FONT=lucida console]~/.local/share/Steam/SteamApps/common/Team Fortress 2/hl2-optirun.sh[/FONT] (without the overlay) and running the game from the Steam client without optirun works normally. Disabling the overlay from the Steam client doesn't resolve this issue.

Has anyone found any resolution to this issue?

Thanks!

---

### Post by zhongfu on 2014-10-11
Apparently something new in xorg-edgers broke it. Used ppa-purge to remove the entire PPA and reinstalled nvidia-331, and now everything's working again. My lightdm also works now too!

---

### Post by anirudhkamineni on 2014-12-03
I am new to Linux and having trouble with the same crash. Could you spare some time and elaborate the steps you took to overcome the errors?
Thank you

---

