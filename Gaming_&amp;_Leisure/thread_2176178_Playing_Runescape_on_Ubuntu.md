---
title: "Playing Runescape on Ubuntu"
date: 2013-09-23
forum: Gaming &amp; Leisure
---

### Post by smithben2012 on 2013-09-23
I have firefox, trying to play runescape. The page loads just fine. but when i click play free now it goes black, slows right down. bottom left corner says transsfering data. then it goes white. there is stiil the things at the bottom of the page, like facebook link etc. game wont load. is it the browser do i need another program? not sure what to do, please help.

---

### Post by mastablasta on 2013-09-23
are you using oracle java?

---

### Post by HikariKnight on 2013-10-03
playing any java game on linux that uses opengl is problematic after java7 got released as you will have to add the java library folder to LD_LIBRARY_PATH before launching the game.

the official runescape wiki have a few methods listed for running the game, everything from running the game client through wine, to unofficial client ports or java-wrappers

easiest would be to install the RuneScape Unix Client port that is under active development by me as it contains several optimization and tweaking options to improve the clients performance
[IMG]http://screencloud.net/img/screenshots/a2250ebaa00036d46ea8e65d869c0c1b.png[/IMG]
[IMG]http://screencloud.net/img/screenshots/02114d17011cb6a63033e08f14703fdf.png[/IMG]

```
sudo apt-add-repository ppa:hikariknight/unix-runescape-client
sudo apt-get update
sudo apt-get install unix-runescape-client
```

---

### Post by enterdavertex on 2013-10-04
Or even try the Open JRE.
**_[COLOR=#000000][FONT=monospace]sudo apt-get install openjdk-7-jre[/FONT][/COLOR]_**

---

