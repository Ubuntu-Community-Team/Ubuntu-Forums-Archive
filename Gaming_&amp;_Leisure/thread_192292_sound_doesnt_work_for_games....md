---
title: "sound doesnt work for games..."
date: 2006-06-08
forum: Gaming &amp; Leisure
---

### Post by Polygon on 2006-06-08
Ok so i recently reinstalled ubuntu 5.10 and then upgraded to dapper like 2 days after. Dapper automatically configured my sound card and installed the correct alsa drivers for it, so i did absoulutely nothing

but, i tried to play the quake 4 demo (just to see if it worked) and the sound is all screwed up. I can hear sound, but i hear this high pitched kind of electronic sound whenever a sound tries to play inside the game. And before i reinstalled, i had the same problem with the Doom 3 demo with ubuntu 5.10 (infact... the exact same problem)

but i also have americas army installed and i can hear sound in that game perfectly...

is there something i have to configure or some libraries i need to isntall before sound can work properly in these games?

thanks!

---

### Post by ironfistchamp on 2006-06-11
I think I had the same problem with Q4 demo. There is a thread floating around here somewhere about it. Anyway using this command fixed it

 quake4-demo +set s_driver oss

You can also edit the menu item for quake (or create one) and use that command. that stopped the stupid electronic noise for me and made it work fine. One thing is that after running amaroK the sound won't work and I have to restart X. Hope this helped.

Ironfistchamp

EDIT: Great now sound doesn't seem to work at all. Linux is great but it is just as random as windows :P

---

