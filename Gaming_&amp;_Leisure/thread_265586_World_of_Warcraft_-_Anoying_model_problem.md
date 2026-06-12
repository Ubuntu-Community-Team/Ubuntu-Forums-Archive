---
title: "World of Warcraft - Anoying model problem"
date: 2006-09-26
forum: Gaming &amp; Leisure
---

### Post by aX- on 2006-09-26
Has anyone else had this problem or know a fix for it?

[img]http://www.users.on.net/~ajcomet/coughwtf.png[/img]

---

### Post by Josh1 on 2006-09-26
I had that problem with windows, turned out to be my graphics card. Stupid thing, had to return it and get a new one. Does WoW work perfectly under windows?

---

### Post by aX- on 2006-09-26
Yeah it works fine in windows. I guess its just the dodgy ati drivers.

I got a ASUS x800 Pro/TVD if that helps

---

### Post by MrZaphod on 2006-09-26
Check the wiki [WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft") but I suspect that you are running WoW in directx mode.

Try adding '-opengl' e.g. 'wine WoW.exe -opengl' and WoW will start in opengl mode.

---

### Post by aX- on 2006-09-26
> **MrZaphod said:**
> Check the wiki [WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft") but I suspect that you are running WoW in directx mode.

Try adding '-opengl' e.g. 'wine WoW.exe -opengl' and WoW will start in opengl mode.

Awesome that worked! thanks.

---

