---
title: "[GUIDE] Quake on Ubuntu"
date: 2012-05-09
forum: Gaming &amp; Leisure
---

### Post by ?#Yhf%*&amp; on 2012-05-09
I made a guide on how to install Quake on Ubuntu for new users. I hope this helps someone! :KS

[http://corbindavenport.blogspot.com/2012/05/installing-quake-on-ubuntu-winquake.html]("http://corbindavenport.blogspot.com/2012/05/installing-quake-on-ubuntu-winquake.html")

I could not figure out how to install a native linux version for the life of me, so this guide uses WinQuake and Wine.

---

### Post by ahso4271 on 2012-05-11
It's been a while, but I think install is about the same as for Doom3:

[http://www.cyberciti.biz/faq/linux-install-doom3-game/](http://www.cyberciti.biz/faq/linux-install-doom3-game/)

---

### Post by blueshead on 2012-05-12
I use ioquake to run quake3..works great!

[http://ioquake3.org/]("http://ioquake3.org/")

---

### Post by leilei on 2012-05-13
Both of you miss the point.

It's about running the original Quake on Ubuntu.


That said, there are various native engines you can try:

Darkplaces
Quakespasm
Quakeforge

I believe there's also a straight SDL port of Quake as well.

---

### Post by dmn_clown on 2012-05-13
Why not just create the games directory's, then copy the game's *.paks to their data folder and drop darkplaces into the games toplevel directory and call it a day?

---

### Post by thatguruguy on 2012-05-13
> **dmn_clown said:**
> Why not just create the games directory's, then copy the game's *.paks to their data folder and drop darkplaces into the games toplevel directory and call it a day?

This. There's no reason to run Quake through Wine, really.

---

### Post by evilate on 2012-07-03
> **thatguruguy said:**
> This. There's no reason to run Quake through Wine, really.

Care to elaborate on that?

The readme is not for complete newbies :)

---

### Post by mastablasta on 2012-07-04
it was explained above: 
create the games directory's, then copy the game's *.paks to their data folder and drop darkplaces into the games toplevel directory

---

### Post by zevans on 2012-07-08
So to explain the explanation...

You need to get hold of the .pak files from the original Quake. I downloaded the shareware installer and ran that in WINE. That unpacks Quake into the ~/.wine/drive_c directory.

However DON'T run Quake now using wine... just tell darkplaces to use that directory, like this:

```
darkplaces -width 1280 -height 768 --base_dir ~/.wine/drive_c/quake
```

In other words you have to tell darkplaces where to find the original Quake data.

So it works - my question is how do I make it look good - can someone recommend a texture pack to take advantage of the new stuff in Darkplaces?

---

### Post by HolgerB on 2012-07-09
[http://fps.maros.pri.ee/index.php?event=1346](http://fps.maros.pri.ee/index.php?event=1346)

---

### Post by Brebs on 2012-07-09
> **zevans said:**
> texture pack
Take a look through e.g. [QuakeOne](http://quakeone.com/).

---

### Post by scar3crow on 2012-12-18
so easy my kitten could do it:
[http://ubuntuforums.org/showthread.php?p=12410681#post12410681](http://ubuntuforums.org/showthread.php?p=12410681#post12410681)

---

