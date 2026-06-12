---
title: "Remote Desktop Question"
date: 2006-03-19
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-03-19
I want to see my desktop at home from my workplace, I have Ubuntu at both the places and remote desktop settings enabled.

At home I have a home router and three computers connected to it. 

How should I make sure that I login the same computer which I intend to.

Right now i am doing

```

vncviewer -fullscreen my_home_ip_address:0

```

Please suggest something if I have to do some setting changesin my home router.

thanks

---

### Post by Zelut on 2006-03-19
All you will need to do is forward port 5900 on your router to the LAN IP of the home machine you want to connect to.

---

### Post by krypto_wizard on 2006-03-19
Thanks a lot, worked like charm !!!



[QUOTE=kuyaedz]All you will need to do is forward port 5900 on your router to the LAN IP of the home machine you want to connect to.[/QUOTE]

---

