---
title: "Caster for Linux"
date: 2009-05-17
forum: Gaming &amp; Leisure
---

### Post by Sealbhach on 2009-05-17
I just saw this game on Softpedia:

[http://www.elecorn.com/caster3d/](http://www.elecorn.com/caster3d/)

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/TBS/Action/Caster-47661.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/TBS/Action/Caster-47661.shtml)

I downloaded the demo, it installed OK but when I tried to run it I got segmentation fault. I'm running 64-bit Jaunty but I'm fairly sure I have all the 32-bit libraries. 

.

---

### Post by Vadi on 2009-05-18
Try contacting support? It's working fine here on 64bit

---

### Post by Sealbhach on 2009-05-18
> **Vadi said:**
> Try contacting support? It's working fine here on 64bit

OK, it's working now, thanks. I just reinstalled it. Not a bad game actually.

.

---

### Post by scorp123 on 2009-05-20
> **Sealbhach said:**
> Caster ...   but when I tried to run it I got segmentation fault. I just experienced the same. In my case it was because "Caster" did not like the location I installed it to.

You have to install the game into your own home directory, e.g. **/home/yourusername/caster**  ...  If you use "sudo" to install it system-wide into e.g. /opt/caster then the binaries will belong to "root" and for some odd reasons you will then experience the error you describe, probably because the program somehow expects the user trying to launch the game and the file ownerships of the game's files to be the same?? IMHO this is a bug. I have other Linux games too (e.g. "World of Goo", "Tee Worlds", etc.) that are installed system-wide manually (/opt/WorldOfGoo, /opt/teeworlds, etc.) and they don't have this problem. So as a workaround you have to install "Caster" inside your own home ... then it will work OK.

---

