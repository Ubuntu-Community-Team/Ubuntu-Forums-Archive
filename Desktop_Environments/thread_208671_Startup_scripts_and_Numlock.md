---
title: "Startup scripts and Numlock"
date: 2006-07-03
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-07-03
Okay. First things first. I run a script to disable Shift+Backspace. I have to hand-run it because when I place it under "System-->Preferences-->Sessions-->Startup" it wont run.
```

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

```

Also, I can't seem to turn on the numlock while starting my computer, and its getting annoying. I can only do it by hand.

---

### Post by aysiu on 2006-07-03
Make sure [have extra repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update
sudo aptitude install numlockx
```

---

### Post by Wr8EYilK8Y on 2006-07-03
I already tried that.

---

### Post by aysiu on 2006-07-03
[QUOTE=Your Name Is]I already tried that.[/QUOTE]
Maybe try the second part of this, then?
[http://ubuntuguide.org/wiki/Dapper#How_to_turn_on_Num_Lock_on_GNOME_startup](http://ubuntuguide.org/wiki/Dapper#How_to_turn_on_Num_Lock_on_GNOME_startup)

---

### Post by jvictor on 2006-07-04
Just installing numlockx dint help me , I'd to run it once from the shell :)

```
#numlockx
```

---

### Post by Wr8EYilK8Y on 2006-07-04
I tried that too. I had that sudden bright spot, no worky. :( I'll try aysiu's link

---

### Post by Wr8EYilK8Y on 2006-07-07
Did not work (any of them). Any ideas?

---

