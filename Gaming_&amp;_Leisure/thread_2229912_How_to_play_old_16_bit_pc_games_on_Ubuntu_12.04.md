---
title: "How to play old 16 bit pc games on Ubuntu 12.04"
date: 2014-06-16
forum: Gaming &amp; Leisure
---

### Post by mo11 on 2014-06-16
i have an old pc game from '98 which a message pops up when i try to run it on Ubuntu 12.04 it says "will only run if your backdrop is set to High Colour (16bit) format." i really want to get it working, can someone please help.  Thanks a lot.

Mo

---

### Post by mastablasta on 2014-06-16
what old PC game? how are you running it?

set the desktop colour to 16bit and try again.

---

### Post by mo11 on 2014-06-16
how do you change it to 16bit on ubuntu 12.04?

---

### Post by mo11 on 2014-06-17
the game is HEDZ n im using the disc, I just need to know how to change the color to 16 bit n if it still doesnt work then thats that, somebody here must know how to get an old pc game to work on Ubuntu

---

### Post by mo11 on 2014-06-17
even Rayman & Glover both dont work, a black screen pops up for a split second like its about to play but then goes away, n yes i installed Wine n they still dont work

---

### Post by sudodus on 2014-06-18
Really old DOS based PC games can be played if you install

[http://www.freedos.org/](http://www.freedos.org/)

I'm sorry, but I don't know how to change to 16 bit colours in Ubuntu. I found this thread
[URL="http://ubuntuforums.org/showthread.php?t=1238639"]
Set Color Depth to 16-Bit[/URL]

Maybe it works for you. In new versions of Ubuntu there might be no **/etc/X11/xorg.conf** file. In such cases you simply create it with the text editor.

---

### Post by mastablasta on 2014-06-18
ah so you are running the games in wine? you didn't say it was a Windows game. then you have to look at wine config file (winecfg i believe). you can also look at wine appd : [https://appdb.winehq.org/](https://appdb.winehq.org/) to see if game was tested , if it runs and for any tips and tricks.

for hedz i found: [http://bugs.winehq.org/show_bug.cgi?id=35666](http://bugs.winehq.org/show_bug.cgi?id=35666)
you could try running it with this command in bug

```
wine HEDZ.EXE  -- :1 -ac -depth 16
```

I am not sure which version of Rayman is it but this one  has gold rating: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=4975](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4975)

if games are DOS based you can just install and use dosbox to run them.

if wine fails and games are not graphically intensive then their is always virtualbox and Windows install inside it.

---

