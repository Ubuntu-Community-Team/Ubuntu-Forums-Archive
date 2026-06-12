---
title: "Failed to start login session after installing gtk+3 then removing it"
date: 2015-08-31
forum: Desktop Environments
---

### Post by rez-dj on 2015-08-31
Ubuntu 14.04 LTS



I used code

sudo apt-get install gtk+3 (a sega emulator required gtk+ to run)

But sega emulator needed more things like SDL..got me confused so i decided to give up & remove gtk as i didn't need it.. So i used

sudo apt-get remove gtk+3

Left it like that without shutdown, next morning, my laptop froze after a while of using it normally, the mouse courser moved but nothing else worked so i had to hard reset...& after that i couldn't login anymore.

Please help me get things back to normal. I'm able to Ctrl+Alt+F1/F2 so there should be a way to fix things using code.. 

Please help.. Thanks..


Edit:

hey i fixed it :D

> sudo apt-get update
sudo apt-get install ubuntu-desktop

---

