---
title: "KQ source problems"
date: 2008-01-16
forum: Gaming &amp; Leisure
---

### Post by Smatt454 on 2008-01-16
I downloaded a fun rpg through the adept software package manager (on Kubuntu 7,10) and it's a pretty fun game. i kind of wanted to play around with the source code, so i downloaded it from the kq website [http://kqlives.sourceforge.net](http://kqlives.sourceforge.net)

before playing around with the source, i tried compiling it, 
```
,/configure
```
```
make
```
```
sudo make install
```
all seem to work fine. no errors. however when i run the executable (from a termintal of just clicking on it) 
i get "Could not load misc.pcx" (which if i'm correct, is a sound file or something)

i tried locating the misc,pcx file
```
locate misc
```
and 
```
locate misc.pxc
```
which came up with nothing.

i even tried 
```
locate *.pcx
```
but i only got alienareana files
```
/usr/share/games/alien-arena/data1/players/martian/aliengrunt.pcx
/usr/share/games/alien-arena/data1/players/martian/helmet.pcx
/usr/share/games/alien-arena/data1/players/lauren/skin.pcx
/usr/share/games/alien-arena/data1/sprites/blood1_0.pcx
/usr/share/games/alien-arena/data1/sprites/blood2_0.pcx
/usr/share/games/alien-arena/data1/sprites/blood3_0.pcx
/usr/share/games/alien-arena/data1/pics/m_background.pcx
/usr/share/games/alien-arena/data1/pics/conback.pcx
/usr/share/games/alien-arena/data1/pics/conchars.pcx
/usr/share/games/alien-arena/data1/pics/pause.pcx
/usr/share/games/alien-arena/data1/pics/backtile.pcx
/usr/share/games/alien-arena/data1/pics/colormap.pcx
/usr/share/games/alien-arena/data1/pics/quit.pcx
/usr/share/games/alien-arena/data1/pics/loading.pcx
/usr/share/games/alien-arena/data1/pics/field_3.pcx
/usr/share/games/alien-arena/data1/pics/yn.pcx
/usr/share/games/alien-arena/data1/models/items/keys/red_key/skin.pcx
/usr/share/games/alien-arena/data1/models/items/keys/pass/skin.pcx
/usr/share/games/alien-arena/data1/models/items/keys/key/skin.pcx
/usr/share/games/alien-arena/data1/models/objects/electroball/skin.pcx
/usr/share/games/alien-arena/data1/models/weapons/v_martian_blast/skin.pcx
/usr/share/games/alien-arena/data1/models/weapons/v_martian_blast/skinold.pcx
```

i also get 2 additional messages when attempting to run the manually compiled  version of kq from the terminal(i have the one adept automatically compiled still on this computer)

```
JACK tmpdir identified as [/dev/shm]
Warning: Cannot convert string "vlines2" to type Pixmap
```

**_[SIZE="5"]PLEASE NOTE[/SIZE]_** I DO still have the automatically compiled version on my computer and it works fine.

this is my first time actually modifying a source code for fun (i've only been using linux for about 3-4 months on a spare computer) but i HAVE compiled software before with source code.

if anyone knows why the executable gives me these errors and can help walk me through it, it would be greatly appreciated

THANKS IN ADVANCED :guitar:

---

### Post by Smatt454 on 2008-01-17
i just helped 2 of my friends at school to try to do this (they have our own computers with kubuntu at school) 

i walked them through this, and told them to do EXACTLY what i did. there were no errors for them.

i have NO idea what's wrong....i'm really in a pickle

---

