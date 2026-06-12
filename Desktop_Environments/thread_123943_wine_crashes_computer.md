---
title: "wine crashes computer"
date: 2006-01-31
forum: Desktop Environments
---

### Post by matei24 on 2006-01-31
i have installed wine with automatix and then when it didnt work i isntalled manually from winehq. after everytihng is installed i can't seem to find it anywhere in applications bar or system, so i go into a terminal and type "wine" as sooon as that happens it tells me that wine is creating a configuration directory in home/user, after 20 seconds the computer freezes, so i have to restart manually.
any ideas?

---

### Post by Sutekh on 2006-01-31
[QUOTE=matei24]i have installed wine with automatix and then when it didnt work i isntalled manually from winehq. after everytihng is installed i can't seem to find it anywhere in applications bar or system, so i go into a terminal and type "wine" as sooon as that happens it tells me that wine is creating a configuration directory in home/user, after 20 seconds the computer freezes, so i have to restart manually.
any ideas?[/QUOTE]
Did you run 'winecfg' after installing wine, as prompted by Automatix?

Wine isn't a program, in that you can 'run' it by using the command 'wine' or by adding it to a panel.

To use wine (after running winecfg), use the command
```
wine /path/to/application/setup.exe
```
to get wine to install your program.

If then you would like a panel launcher/button to run the program once it's installed, you can create one and in the command entry use somthing like this
```
wine "~/.wine/drive_c/Program Files/<Application>/<Application>.exe"
```

---

