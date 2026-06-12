---
title: "need help with dosbox and old games"
date: 2009-01-25
forum: Gaming &amp; Leisure
---

### Post by hempa on 2009-01-25
hi i just installed dosbox and i have downloaded a couple of old games that i want to play (maniac mansion,monkey island and dink smallwood) so i first made a folder in my home dir. that i called dosgames, and i put all my games in that folder.Then i opened dosbox and wrote this command 

mount c /home/myusername/dosgames/  
it works great. And then i cd into lets say dink for example and use the command "dir" i then see all the files in the dink directory but when i choose the dink.exe i get a error mesage saying "this program cannot be run in dos mode" 
i dont know what im doing wrong here maybe im writing the wrong command to start the .exe file. 

if anyone could help me that would be great thanks!

---

### Post by k@e on 2009-01-25
Your application "dink" cannot be run using DOSBox. It looks like it needs Windows at least, so your best bet to get it running are Wine or a virtualized Windows.

---

### Post by Grishka on 2009-01-25
> **hempa said:**
> hi i just installed dosbox and i have downloaded a couple of old games that i want to play (maniac mansion,monkey island and dink smallwood) so i first made a folder in my home dir. that i called dosgames, and i put all my games in that folder.Then i opened dosbox and wrote this command 

mount c /home/myusername/dosgames/  
it works great. And then i cd into lets say dink for example and use the command "dir" i then see all the files in the dink directory but when i choose the dink.exe i get a error mesage saying "this program cannot be run in dos mode" 
i dont know what im doing wrong here maybe im writing the wrong command to start the .exe file. 

if anyone could help me that would be great thanks!

use scummvm ([apt://scummvm]("apt://scummvm")) to play maniac mansion and monkey island. dink smallwood is a windows game, it won't run in dosbox. and if you ever want to play dos games, use a frontend. like this one: [http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/](http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/).

---

