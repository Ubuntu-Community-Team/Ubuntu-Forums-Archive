---
title: "UFO: Alien Invasion missions not working"
date: 2010-11-07
forum: Gaming &amp; Leisure
---

### Post by tastygrue on 2010-11-07
Hello everyone.  I downloaded UFO: AI from GetDeb (The newest version) and I have a problem.  Basically, when I send my soldiers to a mission, it asks me whether I want to enter or do auto-mission.  When I click enter, the music changes, but nothing else happens.  It does work when I do auto-mission.  So, what do I need to do to solve this problem?

---

### Post by GanShun on 2010-11-08
I have this problem too. I'm running ubuntu 10.10. Any help would be greatly appreciated.

---

### Post by Rivoot on 2010-11-10
Just for the record, I'm having this problem as well.  Ok, by reading the game's forum I found out that in order to fix this, you have to create a symbolic link to the game.so file, or just move it to the right folder.   This is what I did, and now seems to be working fine:  sudo ln -s /usr/lib/games/ufoai/base/game.so /usr/share/games/ufoa/base/game.so

---

### Post by tastygrue on 2010-11-10
Thank you so much.  The command works!  There is a small typo though, ufoai instead of ufoa in the last part.  But thank you!  I have played this game before, and now I'm so glad that it works! :)

---

### Post by alin ciolompea on 2010-11-14
> **tastygrue said:**
> Thank you so much.  The command works!  There is a small typo though, ufoai instead of ufoa in the last part.  But thank you!  I have played this game before, and now I'm so glad that it works! :)


Thank you both of you! You deserve 2 cup of cofee!

---

### Post by Win-Smash on 2010-11-30
Thanks  worked great someone should let the people over at [http://ufoai.ninex.info/forum/](http://ufoai.ninex.info/forum/) know. There forum was a little hard to fallow. 

sudo ln -s /usr/lib/games/ufoai/base/game.so /usr/share/games/ufoa[COLOR="Red"]i[/COLOR]/base/game.so

 Have another cup :p

---

