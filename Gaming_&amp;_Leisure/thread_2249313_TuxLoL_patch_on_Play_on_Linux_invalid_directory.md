---
title: "TuxLoL patch on Play on Linux: invalid directory"
date: 2014-10-21
forum: Gaming &amp; Leisure
---

### Post by ahmed20 on 2014-10-21
[SIZE=3][FONT=arial][COLOR=#333333]I am following [this howto]("http://askubuntu.com/questions/459888/shop-and-in-game-item-shop-not-working-in-league-of-legend-lol/461256#461256") described by [renatov]("http://askubuntu.com/users/218356/renatov") to install LoL on ubuntu 14.04
[/COLOR]
[COLOR=#333333]I did as shown in the same tutorial i think..[/COLOR]
[COLOR=#333333]
so i get to the patching part:[/COLOR]

```
mono tuxlol.exe patch --dir "~/.PlayOnLinux/wineprefix/LeagueOfLegends/dosdevices/c:/Riot Games/League of Legends"
mono tuxlol.exe patch --dir "~/.PlayOnLinux/wineprefix/LeagueOfLegends/drive_c/Riot Games/League of Legends"
```
[COLOR=#333333]
have tried both lines separately. What i get when i run either is:[/COLOR]

```
The specified directory is invalid. 

```[/FONT][/SIZE]

---

### Post by reid2 on 2014-10-21
I had this problem too. Using this: [COLOR=#444444][FONT=UbuntuRegular]"mono tuxlol.exe patch --dir ~/.PlayOnLinux/wineprefix/LeagueOfLegends/dosdevices/c:/Riot\ Games/League\ of\ Legends/" fixed it for me.[/FONT][/COLOR]

---

### Post by PotatoHead007 on 2014-10-23
Apparenty tuxlol is no longer needed... all i did was edit "[COLOR=#444444][FONT=UbuntuRegular]Riot\ Games/League\ of\ Legends/Config/game.cfg",[/FONT][/COLOR][COLOR=#000000][FONT=UbuntuRegular] [/FONT][/COLOR][FONT=UbuntuRegular]by adding[/FONT][COLOR=#000000][FONT=UbuntuRegular] [/FONT][/COLOR]"[COLOR=#808080]x3d_platform=1[/COLOR]" to the [General] section. My league works flawlessly now. Using the PlayOnLinux install, but changed the wine version to 1.7.24-LeagueOfLegendsCSMT

---

