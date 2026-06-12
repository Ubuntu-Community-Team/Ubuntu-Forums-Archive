---
title: "Game exit if try to use setting meny?"
date: 2014-02-05
forum: Gaming &amp; Leisure
---

### Post by Cerberus90 on 2014-02-05
Hi, i have install Estranged and after that Half-Life demo, Selena and   Team Fortress 2 and game by it self get out on desktop if i try to get in settings meny of options. Also notice that  Estranged in lauch meny (Ubuntu 12.04) have Selena icon and name but on  Ubuntu 2d not?      

[http://steamcommunity.com/app/440/discussions/0/558747287239838633/](http://steamcommunity.com/app/440/discussions/0/558747287239838633/)

---

### Post by dannyboy79 on 2014-02-07
are you saying the estranged act 1 game crashes out and returns you to your desktop IF you try to change any of the settings? sorry, it's tough to read what you're issue since i'm assuming english isn't your native langauge

---

### Post by Cerberus90 on 2014-02-07
Yes it exit on desktop, and show no error message or something that can indicate what is problem, it is all with game with Source engine...

---

### Post by dannyboy79 on 2014-02-07
ok, open a terminal and navigate to where the game is stored, most likely within your home directory hidden folder. the full path is ~/.local/share/steam/steamapps/common/gamenamehere
then try to launch the game from the terminal, most likely something like 
[code]./hl2_linux[code]
should start the game and from there you should be able to see any errors within the terminal output. if you can, get into the settings immediately and turn off film grain and anything that is graphic intensive. what graphics card are you using and what drivers do you have installed.

---

### Post by Cerberus90 on 2014-03-03
Hi now Estranged  work but TF2 not, and also Desura client exit if try sometnig like install game etc... Can you give me exactly command for run game inside terminal...
Also i using Nvidia gt 520 MSI card, with nvidia driver...
[SIZE=5]**EDIT:**[/SIZE]
oK, i try and get this[ATTACH=CONFIG]250929[/ATTACH]

---

