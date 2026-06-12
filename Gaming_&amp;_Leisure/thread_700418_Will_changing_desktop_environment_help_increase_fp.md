---
title: "Will changing desktop environment help increase fps in tremulous ?"
date: 2008-02-18
forum: Gaming &amp; Leisure
---

### Post by genbuntu on 2008-02-18
Hi 
I'm a big fan of Tremulous (an fps game with rts elements :) ).
However, my laptop is a bit old and not able to give that push in terms of fps (I've kept the game graphics (textures etc.) to a minimum).
So I was wondering whether changing to a lighter desktop environment (like xfce or icewm) can help increase the fps ?
Thx.

---

### Post by Ardrias on 2008-02-18
It could perhaps help a bit. You could try the instructions [here]("http://ubuntuforums.org/showthread.php?t=51486") for more fps.

---

### Post by mivo on 2008-02-18
If you are using Compiz-Fusion, turning it off when you start the game will definitely help. This can be done with a script, so that it isn't very tedious, like so:

#! /bin/bash
metacity --replace &
# kwin --replace &  if you use KDE
sleep 2
./<name of the Tremulous executable> &&
sleep 2
compiz --replace &

(If you need an explanation, don't hesitate to ask. :))

---

