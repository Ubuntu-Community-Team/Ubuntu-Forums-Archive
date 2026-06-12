---
title: "Only mouse and wallpaper in Ubuntu 12.04! Please, help!"
date: 2012-12-26
forum: Desktop Environments
---

### Post by lukapez on 2012-12-26
So, i have a problem. Everything was working just fine, and I wanted to integrate social networks into Unity. I found the tutorial and did it. I got bored with them, so I wanted to remove them, but I had no idea how to do it. I went to the software center, typed in unity-webapps, and removed all of the three packages that were shown on the list. After the reboot and login, i had no Unity and no upper column (with wirelles and stuff). I still dont have any of it. I opened the terminal (with keyboard) and Firefox, and now I am asking for your help. Anyone?

---

### Post by N00b-un-2 on 2012-12-26
sounds like you may have nuked your unity environment.  Try dropping to a login shell (ctrl+alt+f1) and assuming you can connect to the internet from there, install the gnome-session-fallback.  Try booting into that, and if it works try reinstalling Unity.

---

### Post by lukapez on 2012-12-26
how do i do that?
i dont know much about linux, im a noob :/

---

### Post by N00b-un-2 on 2012-12-26
if you can open a terminal type 
```
sudo apt-get install gnome-session-fallback
```

then log out, and log back in selecting the fallback session at the log in screen (click on the little Ubuntu logo next to where you type your password and a drop down menu will appear with the session options.  select Gnome Classic)

---

### Post by lukapez on 2012-12-26
i solved it! thanks!
ive found a tutorial on reinstalling unity so i did it that way, and it it works :)

---

