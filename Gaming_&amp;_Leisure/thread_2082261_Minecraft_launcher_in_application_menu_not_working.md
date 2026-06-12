---
title: "Minecraft launcher in application menu not working."
date: 2012-11-08
forum: Gaming &amp; Leisure
---

### Post by Champlin93 on 2012-11-08
In the past I've been able to add a Minecraft launcher in the application menu using the command:
```
java -jar ~/.minecraft/minecraft.jar
```
Witch works perfectly in the terminal but now for some reason in 12.10 this no longer works in the application menu. Why would it work in the terminal but not in the application menu?

---

### Post by DarkAmbient on 2012-11-09
My guess would be that it's trying to run Minecraft from the folder the launcher is at, migh be wrong though. try change the small script to

```
cd ~/.minecraft
java -jar minecraft.jar
```

Feel free to try my installer as well. It'll add Minecraft to your menu, and you can generate more launchers wherever you like too.

---

### Post by Champlin93 on 2012-11-09
I think that's what was happening, I changed it to the full directory

---

