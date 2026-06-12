---
title: "Doom II on ubuntu?"
date: 2010-05-26
forum: Gaming &amp; Leisure
---

### Post by zakshdw on 2010-05-26
hey guys, was just burrowing through some old games and wondered if doom II could play on ubuntu. i'm a pretty big noob so im pretty useless with these things :confused:

---

### Post by hikaricore on 2010-05-26
Yep and there are tons of different doom engines to play with.
My favorte is Doomsday however it's one of the more complex to configure and install.
Prboom is in the repos and it should work just fine with doom2.

---

### Post by RabidWeezle on 2010-05-27
```
sudo apt-get install prboom
```
get doom2.wad off your cd/floppies somehow (dosbox might work well for that). make sure the name is doom2.wad not DOOM2.WAD then copy it to the proper folder:

```
sudo cp doom2.wad /usr/share/games/doom/doom2.wad
```
then whenever you want to play:
```
prboom
```

---

### Post by matthekc on 2010-05-27
Most old dos games run in DOSBox.

---

### Post by kellylapointue on 2010-05-27
I had that running last year, should be ok

---

### Post by zakshdw on 2010-06-07
cheers guys :) just type 

sudo apt-get install DOSBox? :P

---

### Post by zakshdw on 2010-06-07
okay so i got my WAD and im really not sure how to copy it to the directory needed

every time i dry to copy and paste it or drag and drop, it says 

There was an error moving the file into /usr/games

Error moving file: Permission denied

:confused:

---

### Post by Rustybolts on 2010-06-07
sudo nautilus
in terminal then you can drag n drop

---

