---
title: "World Of Warcraft"
date: 2007-03-20
forum: Gaming &amp; Leisure
---

### Post by irishman869 on 2007-03-20
Ok heres the deal i have loaded WOW on my computer and when i start it the program up then it is really really slow.  Not in game but just the login screen.  On average it takes about 10 seconds for the mouse to move each time i move it.  My current dilemma is how do i correct this.  I have a Dell Inspiron 8600 with the Intel Celeron M 1.7ghx processor and a 256mb Nvidia GeForce FX video card and about 512mb of RAM

---

### Post by MattThLinuxNewb on 2007-03-20
Have you got the nvidia graphics driver for linux? Go to the Synaptic Package Manager (System > Administration > Synaptic) and search for the name 'nvidia'.  Also, are you running WOW in opengl mode? To do this you have to edit the config.wtf file in the World\ of\ Warcraft/WTF directory. Just add/change this line to the file:
```

SET gxApi "OpenGL"

```
I just followed this guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
Hope this is of some help.

---

### Post by irishman869 on 2007-03-20
i saw that on there but the file doesnt exist and i cant go into the game cause its way to slow.  not even the game itself just the login screen.  i havent been past that point

---

### Post by hikaricore on 2007-03-20
```
wine WoW.exe -opengl
```

FTW

---

### Post by irishman869 on 2007-03-20
a message came up saying "module not found"

---

### Post by hikaricore on 2007-03-20
You should be running this command from a terminal inside the WoW directory.

```

cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
wine WoW.exe -opengl
```

If you're running it FROM the WoW directory, you shouldn't get that kind of error.

---

