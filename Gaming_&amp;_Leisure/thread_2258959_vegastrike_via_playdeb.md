---
title: "vegastrike via playdeb"
date: 2014-12-31
forum: Gaming &amp; Leisure
---

### Post by CYzMLcT on 2014-12-31
Hello, I recently installed vegastrike from the playdeb repositories on my computer (ubuntu 14.04) Playdeb has the most recent stable version (0.5.1.r1), and installation went fine (no warnings about dependecies) whenever I run the game however, it brings up the loading screen, loads some files, and then crashes, leaving my desktop completely destroyed by scaling issues (easily fixed by restarting) I ran vegastrike from a terminal and recorded the output, it is as follows:
```
Script started on Mon 29 Dec 2014 11:43:07 AM PST
]0;me@me-Desktop: ~me@me-Desktop:~$ vegastrike 
Registering codec ogg. 
 In path /usr/games 
Vega Strike   
See http://www.gnu.org/copyleft/gpl.html for license details. 
 
GOT SUBDIR ARG =  
Found data in /usr/share/games/vegastrike 
Using /usr/share/games/vegastrike as data directory 
Using .vegastrike as the home directory 
Found MODDIR = /usr/share/games/vegastrike/mods 
USING HOMEDIR : /home/me/.vegastrike As the home directory  
CONFIGFILE - No config found in home : /home/me/.vegastrike/vegastrike.config 
CONFIGFILE - No home config file found, using datadir config file : /usr/share/games/vegastrike/vegastrike.config 
DATADIR - No datadir specified in config file, using ; /usr/share/games/vegastrike 
SIMULATION_ATOM: 0.05 
MISSION_NAME is empty using : main_menu.mission 
Attempt to call ReadFull on a bad file units.csv -1 /usr/share/games/vegastrike/units/units.csv 
running import sys 
print sys.path 
sys.path = [r"/usr/share/games/vegastrike/modules/builtin",r"/usr/share/games/vegastrike/modules/quests",r"/usr/share/games/vegastrike/modules/missions",r"/usr/share/games/vegastrike/modules/ai",r"/usr/share/games/vegastrike/modules",r"/usr/share/games/vegastrike/bases"] + sys.path 
['/usr/lib/python2.7/', '/usr/lib/python2.7/plat-x86_64-linux-gnu', '/usr/lib/python2.7/lib-tk', '/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload'] 
testing VS randomrunning import sys 
print sys.path 
['/usr/share/games/vegastrike/modules/builtin', '/usr/share/games/vegastrike/modules/quests', '/usr/share/games/vegastrike/modules/missions', '/usr/share/games/vegastrike/modules/ai', '/usr/share/games/vegastrike/modules', '/usr/share/games/vegastrike/bases', '/usr/lib/python2.7/', '/usr/lib/python2.7/plat-x86_64-linux-gnu', '/usr/lib/python2.7/lib-tk', '/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload'] 
Creating scene manager... 
Creating template manager... 
  Initializing renderer... 
setting joystick functionality:: joystick onlineGlut detects 1 joystickaxes: 3 buttons: 15 hats: 0 
axes: 3 buttons: 15 hats: 0 
FactionXML:LoadXML factions.xml 
*** buffer overflow detected ***: vegastrike terminated 
Segmentation fault (core dumped) 
]0;me@me-Desktop: ~me@me-Desktop:~$ exit 
exit 

Script done on Mon 29 Dec 2014 11:43:32 AM PST
```
I am not sure what a segmentation fault means, but it seems to be responsible. I found "factions.xml" and opened it, it appears to be normal (not obviously corrupted), so I doubt that that is the problem.

Any help would be appreciated, I look forward to playing this game!

---

### Post by CYzMLcT on 2015-01-01
Update: I can get the game to run by running "sudo rmmod joydev" before starting the game. Anyone have any idea of how to get the game to work without disabling the joystick?

---

