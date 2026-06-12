---
title: "CS source"
date: 2007-07-13
forum: Gaming &amp; Leisure
---

### Post by cytg on 2007-07-13
Hope this is not too trivial.

here's the thing .. i've found the winehq database and all the instructions for installation etc.
However, at present time, i have no idea where my cdkey is. It is however happily residing in some form on my windows partiion and i figure in the steam directory somewhere.
So this is what i want to do, copy the game directory to my ubuntu disc and run it from there, thus keeping the cdkey intact.
But when i execute steam, the splash login screen is not showing correctly, just some graphics but no text at all .. looks sorta naked.

Is what im trying to do .... doable at all ?

---

### Post by dfreer on 2007-07-13
First off, you don't need your CD-Key anymore. Once you install steam and create a username/password (I assume you've done this in windows), any games you buy/register will be tied to your username. So steam will "know" you already have these games, and on any computer anywhere, as long as you login to steam you will be able to redownload and play these games (even if your original game came on a CD, you can still download a copy). 
However, if you don't want to spend the time downloading the games all over again, you can copy your steamapps folder from the steam directory in windows (normally C:\Program Files\Steam) to the steam directory in linux (normally ~/.wine/drive_c/Program\ Files/Steam/). 
As for the text issue, this is well known issue, wine appdb should've had the solution. Basically, you will need to copy the font tahoma.ttf to your wine fonts folder. You can find tahoma.ttf in your windows partition or *somewhere* online. It will need to be put in ~/.wine/drive_C/windows/fonts/

---

### Post by cytg on 2007-07-17
Thanks .. ill give it a shot :)

---

