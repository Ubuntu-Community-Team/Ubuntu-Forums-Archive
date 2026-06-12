---
title: "Run Cedega without P2P?"
date: 2005-10-28
forum: Desktop Environments
---

### Post by rj686 on 2005-10-28
I found a cedega debian package on my old computer, but alas no point 2 play package. I no longer have the access to an account to pay for p2p, but is there a way to run cedega without using p2p?

---

### Post by psychicdragon on 2005-10-28
Sure, It works just like wine: **cedega program.exe**

You can create launchers for your games if you want.

---

### Post by rj686 on 2005-10-28
is there like a "cedegacfg" command to change the config since i dont have the gui of p2p?

---

### Post by bryan986 on 2005-10-28
the config is the file ~/.transgaming/config

---

### Post by rj686 on 2005-10-28
thx :)

---

### Post by rj686 on 2005-10-29
is there a way to change where cedega looks for games by default...... because its looking in the wrong folder for games. I mean i know i can manually create a launcher i was just looking for something simpilar like cedega "StarCraft" for instance

---

### Post by psychicdragon on 2005-10-29
Not that I know of. Cedega only looks in the current directory unless a path is specified. How hard is it really to create a launcher though?

If you notice that Starcraft is running poorly, like the mouse moves really slowly. You'll want to launch Starcraft using nice -20, which gives it the highest scheduling priority.
```
nice -20 cedega "/home/**username**/.transgaming/c_drive/Program Files/Starcraft/starcraft.exe"
```

---

### Post by rj686 on 2005-10-29
thx......its not hard to create a launcher, i've done it with the games. I was just curious thats all. For some reason cedega was looking in "/usr/lib/transgaming_cedega//winex/bin/wine" i dunno why though........ 

Thx for teh info :)

---

