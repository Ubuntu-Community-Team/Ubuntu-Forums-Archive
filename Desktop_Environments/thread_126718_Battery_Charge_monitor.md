---
title: "Battery Charge monitor?"
date: 2006-02-07
forum: Desktop Environments
---

### Post by Mastershredder on 2006-02-07
Is there a Battery Charge monitor built into Kubuntu, like the one in Ubuntu? I'm not finding one if there is. Its not very fun when your laptop starts flashing cause you don't know what the power level is at :P

---

### Post by dresnu on 2006-02-07
[QUOTE=Mastershredder]Is there a Battery Charge monitor built into Kubuntu, like the one in Ubuntu? I'm not finding one if there is. Its not very fun when your laptop starts flashing cause you don't know what the power level is at :P[/QUOTE]

Kmenu-> System Settings-> Laptops & Power-> Laptop Battery ->Show battery monitor

---

### Post by Mastershredder on 2006-02-07
Hmm.. when I click the Kmenu, I don't have system settings. Just System and Utilities come close to that. I tried checking Kcontrol under Desktop, Panels and I don't see any optional menus called System Settings. I can't find anything with Laptop in the name either.

---

### Post by dresnu on 2006-02-07
Ok then try this: ```
sudo apt-get install klaptopdaemon
```

Then go to Kcontrol-> Power Control-> Laptop Battery-> Show battery monitor

---

### Post by Mastershredder on 2006-02-07
Thanks a ton. Worked like a charm. I hate being a noob ;)

---

### Post by dresnu on 2006-02-07
Glad it worked ;). Hey, I'm noob too lolz

---

