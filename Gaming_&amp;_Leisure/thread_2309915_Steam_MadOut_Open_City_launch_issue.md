---
title: "Steam MadOut Open City launch issue?"
date: 2016-01-14
forum: Gaming &amp; Leisure
---

### Post by aleksander7 on 2016-01-14
Just installed Steam on my Ubuntu 16.04 64-bit, downloaded and installed MadOut Open City. When I try to launch it the screen just flashes and nothing happens. I know there are some problems with running steam on 64-bit...
I have no clue what I need to do to get it working so any help is much appreciated!


Game update: AppID 428190 "MadOut Open City", ProcID 31701, IP 0.0.0.0:0
ERROR: ld.so: object '/home/aleksanderbn/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/aleksanderbn/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Found path: /home/aleksanderbn/.local/share/Steam/steamapps/common/MadOut_OpenCity/game.x86_64
Mono path[0] = '/home/aleksanderbn/.local/share/Steam/steamapps/common/MadOut_OpenCity/game_Data/Managed'
Mono path[1] = '/home/aleksanderbn/.local/share/Steam/steamapps/common/MadOut_OpenCity/game_Data/Mono'
Mono config path = '/home/aleksanderbn/.local/share/Steam/steamapps/common/MadOut_OpenCity/game_Data/Mono/etc'
displaymanager : xrandr version warning. 1.4
client has 3 screens
displaymanager screen (0)(LVDS1): 1366 x 768
Using libudev for joystick management


Importing game controller configs
Game removed: AppID 428190 "MadOut Open City", ProcID 31701

---

### Post by aleksander7 on 2016-01-14
I also have Robocraft wich works flawlessly but I also get this log on that game.

Game update: AppID 301520 "Robocraft", ProcID 32631, IP 0.0.0.0:0
ERROR: ld.so: object '/home/aleksanderbn/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/aleksanderbn/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Found path: /home/aleksanderbn/.local/share/Steam/steamapps/common/Robocraft/Robocraft.x86_64
Mono path[0] = '/home/aleksanderbn/.local/share/Steam/steamapps/common/Robocraft/Robocraft_Data/Managed'
Mono path[1] = '/home/aleksanderbn/.local/share/Steam/steamapps/common/Robocraft/Robocraft_Data/Mono'
Mono config path = '/home/aleksanderbn/.local/share/Steam/steamapps/common/Robocraft/Robocraft_Data/Mono/etc'
displaymanager : xrandr version warning. 1.4
client has 3 screens
displaymanager screen (0)(LVDS1): 1366 x 768
Using libudev for joystick management


Importing game controller configs
Installing breakpad exception handler for appid(gameoverlayui)/version(20151214111647)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Game removed: AppID 301520 "Robocraft", ProcID 32633

---

