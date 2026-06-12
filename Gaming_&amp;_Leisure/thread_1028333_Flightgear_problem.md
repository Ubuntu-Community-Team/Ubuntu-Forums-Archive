---
title: "Flightgear problem"
date: 2009-01-02
forum: Gaming &amp; Leisure
---

### Post by Omecron on 2009-01-02
I am wanting to install some planes to fly and the directory I need to put them in I can not change as my normal lowly user self. I know I can go to terminal and sudo then copy everything, but is there a way I can use a GUI and be sudo then just turn it off.

Please don't think me lazy, I am just getting addicted to flightgear and I see this becoming a daily thing  :D

I swear I do think I ran a GUI as sudo somehow way back, but I had been going back to XP to play games with my wife. XP finally got so bad with SP3 she gave her blessing for Linux and I am here, but my memory just stinks....

---

### Post by Schok on 2009-02-01
bump. i got the models but i dont know where to put it too

---

### Post by lenzoid on 2009-02-02
Making the Aircraft folder writable to you would save you sudoing efforts.  I usually do that for games, even if its not the perfect, secure unix-like way yet I dont care much about that when it comes to directories containing game files.

```
 sudo chown `whoami` [[ flightgear dir/Aircraft ]]
```

Unfortunately, fgfs doesn't support deploying game data files in your home dir.... which would have been the perfect userland solution and is an option for many games

---

