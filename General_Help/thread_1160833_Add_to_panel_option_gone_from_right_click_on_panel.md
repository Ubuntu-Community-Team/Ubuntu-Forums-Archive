---
title: "Add to panel option gone from right click on panel."
date: 2009-05-16
forum: General Help
---

### Post by XxsydenxX on 2009-05-16
I was messing around in the gconf....trying to set a custom icon for the menu bar in ubuntu but i failed...is there anyway to get things to default??

---

### Post by ninjapirate89 on 2009-05-16
Can you still right-click and create a new panel? It is probably easiest to create a new panel then delete the one that is giving you trouble. Of course then you will have to start from scratch but AFAIK that is the only way to reset it to the original.

---

### Post by XxsydenxX on 2009-05-16
No i get no options other then. Help and about panels.

---

### Post by ninjapirate89 on 2009-05-16
Hmmm... never seen that before. Try this in a terminal:
```

killall gnome-panel

```

This will stop gnome-panel from running. It will start again automatically.

---

### Post by XxsydenxX on 2009-05-16
The problem still exists.

---

### Post by ninjapirate89 on 2009-05-16
Have you tried restarting? Other than that I'm at a loss. I've never had this problem before.

---

### Post by XxsydenxX on 2009-05-16
I have tried restarting, like I said im pretty sure its when i was half asleep messing with the gconf...as root...so simply put i need to get gconf to default of 9.04, im pretty sure anyways...

---

### Post by ninjapirate89 on 2009-05-16
You could try this:
[http://www.ubuntued.com/?p=8]("http://www.ubuntued.com/?p=8")
I've never done it so I can't guarantee it will work so I highly recommend making a backup as it suggests before you try this.

Edit-> If you want I can try it first. Just let me know.

---

### Post by XxsydenxX on 2009-05-16
Worked like a charm, much appreciated..NOW, maybe you could help me with this one other problem i've been having, i would appreciate it very much so...Im truing to change the little ubuntu icon on the menu up top, ive seen a frew tutorials on how to do it in gconf...but honestly they never work for me, any advice?


Edit: let me explain, i have a severe case of OCD and the color orange just drives me insane >_>;

---

### Post by ninjapirate89 on 2009-05-16
I think ubuntu-tweak has the ability to do this. Just type in the terminal:
```

sudo apt-get install ubuntu-tweak

```

Edit -> Sorry thats wrong. Give me a minute I'll find what I'm thinking of.

---

### Post by XxsydenxX on 2009-05-16
I've tried ubuntu tweak but it fails to do it for some reason...trying to use a 24 by 24 image

---

### Post by ninjapirate89 on 2009-05-16
Hmmm....That's the only thing I know to try. Sorry. Have you tried creating a thread for this topic? Maybe someone else has the knowledge.

---

### Post by XxsydenxX on 2009-05-16
I most likely will create another topic now..
thanks again for your help.

---

