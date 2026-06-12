---
title: "Integrate wine into desktop environment"
date: 2009-09-06
forum: Desktop Environments
---

### Post by irielion on 2009-09-06
Hi People,

Recently I started using some windows applications under wine again and I wanted it to integrate as good possible. In this mini tutorial I explain the steps I take to integrate wine programs in to ubuntu. This tutorial assume some basic shell knowledge. I use both playonlinux and normal wine, so i wrote two methods.

**What does it do?**

- Add font antialising
- All fonts
- Icon themes (Gnome, tango, industrial, tangerine) through Tango Icon Patcher
- Current gnome color theme

**PlayOnLinux method:**

1. Install Playonlinux from [http://www.playonlinux.com](http://www.playonlinux.com)
2. Install your programs
3. In playonlinuInstall programs -> Other -> Microsoft fonts
4. Install programs -> Other -> Font antialising

**Normal method:**

1. Create wineprefix: ```
WINEPREFIX=~/<pathtoprefix> wineprefixcreate
```
2. Download winetricks with the command: ```
wget http://www.kegel.com/wine/winetricks
```
3. ```
sh winetricks fontsmooth-rgb
```
4. ```
sh winetricks allfonts
```

**Final step for both methods:**

5. Download tango patcher from this [link]("http://www.deviantart.com/download/27940418/Tango_Patcher_2600_8_06_by_vertigosity.rar")
6. Unrar and Start tangopatcher with the right wineprefix (i.e. WINEPREFIX=<pathtoprefix> or in PlayOnLinux select the right prefix)
```
WINEPREFIX=pathtoprefix wine <pathtotangopatcher>.exe
```
7. Download wine_colors_from_gnome.py from attached files
8. Open console, type: ```
WINEPREFIX=<pathtoprefix> python wine_colors_from_gnome.py
``` (in PlayOnLinux the prefixes are in ~/.PlayOnLinux/wineprefix)

All done!

---

