---
title: "[SOLVED] FPS Problems in Q3A"
date: 2008-05-29
forum: Gaming &amp; Leisure
---

### Post by Vinnster04 on 2008-05-29
Problem:  A few days ago I installed Quake 3 Arena on my fresh install of Ubuntu 8.04 Hardy. Ran into problems cuz I am running a 64 bit processor, however I managed to get that working. Also had a problem with no sound in the game, got that working also. So my problem is when I am playing Q3A, I have very low fps. First it started with 20 to 30 fps. Then I installed EnvyNG reinstalled my nvidia drivers. After I did that, my fps went up to 40 to 60 fps. I have even changed the maxfps in Q3A to 125. I also have the same graphics card running in Windows XP MCE. In Windows, my fps is perfectly fine. I get perfect 125fps in Windows. What could cause this??


Info About My System:  Currently running Ubuntu Hardy 8.04. AMD 64 Athlon processor. Nvidia GeForce FX5500 Graphics Card with 256MB Memory. Computer is dual-booting between Ubuntu and Windows XP MCE. Typical software updates as they pop up on my computer.


Info About Me: Am a complete noob at linux. :P Played with it a little bit about 5 or 6 years ago in High School. Would greatly appreciate if anyone could help me out with this issue(perhaps with simple instructions since I am still trying to get used to linux :P).

---

### Post by Perfect Storm on 2008-05-29
The first thing I would try is disable compiz. Compiz and games works poorly together atm.

Open the terminal and type;
```
metacity --replace
```

Now try run Q3 again.

---

### Post by Vinnster04 on 2008-06-02
It helped somewhat thanks. It jumped my fps to about 80 to 90 now which is way better than before. So do I have to use that command every time I restart my computer or is it permanent? Any other ideas to help this problem?

---

### Post by Perfect Storm on 2008-06-02
To disable compiz
```
metacity --replace
```


to enable compiz
```
compiz --replace
```

Or by installing fusion-icon and make a startup session for fusion-icon you can point'n'click instead.

Third option is to make a script which disable compiz, starts Q3. When exiting Q3 it starts compiz up again.
Check this guide (for another game under launcher) how you can do it: [http://gaming.gwos.org/doku.php/guides:64bit:fizzball](http://gaming.gwos.org/doku.php/guides:64bit:fizzball)

---

### Post by Vinnster04 on 2008-06-04
Ok cool thanks. However I am baffled by another problem. The brightness in Q3A. I of course play the ExcessivePlus mod and I have my brightness set rather high in the game to obviously see more and better. The problem is that during the middle of a map being played, the brightness goes back to default which is dark as crap and can't see anything. But after the map ends and the new map loads, my brightness goes back to where I have it set. Then halfways into the map it goes back to default again. What could cause this??

I have talked to the people from that mod that run linux also, and they switched from ubuntu to debian cause they were having similar problems with Q3A as well, such as low fps and brightness changing at random. Is there solution for this? Or is it just software or hardware compatibility issues or what?

Any info or help would be greatly appreciated. Cuz I really don't wanna do what others have done and switch, I have become accustomed to the feel and look of ubuntu. And I am praying there is a solution cuz ubuntu rox I think anyways. But what do I know, I'm still a noob to the linux atmosphere. :P

---

