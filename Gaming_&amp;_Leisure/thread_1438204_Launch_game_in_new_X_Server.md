---
title: "Launch game in new X Server"
date: 2010-03-24
forum: Gaming &amp; Leisure
---

### Post by Drunken Pirate on 2010-03-24
I want to launch World of Warcraft in a separate X server. I can get the game to launch but I am having two problems:
1) No sound in the game.
2) My nvidia settings are not being properly loaded. (Digital vibrance is not being applied to this new x server.)

Here is the script I am currently using:

```
#!/bin/sh 

X :3 -ac & nvidia-settings --load-config-only 

# Goto game dir (modify as needed)
cd "/home/brent/.wine/drive_c/Program Files/World of Warcraft/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
ck-launch-session
DISPLAY=:3 WINEDEBUG=-all padsp wine Wow.exe -opengl
``` 

Thanks for any input you have,

Brent

---

### Post by Ferrat on 2010-03-24
I think sound can be helped by making WINE use OSS instead in winecfg not 100% and the nVIDIA settings probably doesn't load because the nVIDIA config isn't being applied to the new X server, you might have to lauch the server with some extra settings.

---

### Post by Drunken Pirate on 2010-03-24
Yea I have tried OSS to no avail. (It doesn't work in the new X server, and crackles in the standard X server.) I realize it isn't loading the nvidia config, how can I configure it on the new server/force it to load the config?

---

