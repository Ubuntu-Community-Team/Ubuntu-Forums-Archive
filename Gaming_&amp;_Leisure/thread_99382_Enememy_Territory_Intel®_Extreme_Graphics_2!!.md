---
title: "Enememy Territory Intel® Extreme Graphics 2!!"
date: 2005-12-05
forum: Gaming &amp; Leisure
---

### Post by kruseborn on 2005-12-05
Hi have an Lap top nx 9030 with the graphic card Intel® Extreme Graphics 2.
When I am starting the game enemy territory the screen turn black.
Is it wrong with my graphic drivers or is it something else.

/Tobbe Sweden

---

### Post by newuser111 on 2005-12-05
thats an integrated card not really suited for gaming, but i think it should work

did you try **sudo dpkg-reconfigure xserver-xorg**

---

### Post by Zimmer on 2005-12-05
Kruseborn..it is probably a sound issue.

See my reply here to a previous post..
[http://ubuntuforums.org/showthread.php?t=80926&page=2](http://ubuntuforums.org/showthread.php?t=80926&page=2)
look for reply #14
..and have a look here, too
[https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

I had the same problem (on Fedora core 3, too, and I installed Ubuntu to ty and sort it) and spent a good few hours(days)swapping NVidia  and ATI cards between computers to no avail..until I ran ET from the terminal and managed to access the terminal hidden behind the black screen..and the output gave the message that the sound module was not loaded...
So try the sound fix first...
Regards

Zimmer

---

### Post by Burkey on 2005-12-06
Or it is the same problem I face posted elsewhere on this forum and without a solution as yet.  It seems to be a problem with Intel Integrated drivers on Ubuntu in general.

For me it worked fine on Hoary, Breezy however fails to run 90% of OpenGL apps.

Sound is working fine for me as I hear the into music, can hit esc and then hear the menu music.. to exit just type in ~ (tilde) and  /quit

---

### Post by kruseborn on 2005-12-06
It is not a sound problem, I think its something wrong with the Intel Integrated drivers.
So the problem has been up before with the intel drivers. 
I think its strange it does not work because the graphic card works good in everything else. but this is the first game I test to play in linux, I have tested to play the game in windows and it does work but i realy would like to play ET in ubuntu because windows realy suck:)

Thanks for the replies

---

### Post by kruseborn on 2005-12-06
[QUOTE=newuser111]thats an integrated card not really suited for gaming, but i think it should work

did you try **sudo dpkg-reconfigure xserver-xorg**[/QUOTE]

Ya I know, the card is not good, and its absolutly not suidet for gaming, but its works ok in windows xp. Thats why I think it should work in linux to.
I have tested sudo dpkg-reconfigure xserver-xorg. but I have still the same problem. 
I think its strange that the screen just turn black. Its gives no errors or anything, its just black.

---

### Post by kruseborn on 2005-12-06
[QUOTE=Zimmer]Kruseborn..it is probably a sound issue.

See my reply here to a previous post..
[http://ubuntuforums.org/showthread.php?t=80926&page=2](http://ubuntuforums.org/showthread.php?t=80926&page=2)
look for reply #14
..and have a look here, too
[https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

I had the same problem (on Fedora core 3, too, and I installed Ubuntu to ty and sort it) and spent a good few hours(days)swapping NVidia  and ATI cards between computers to no avail..until I ran ET from the terminal and managed to access the terminal hidden behind the black screen..and the output gave the message that the sound module was not loaded...
So try the sound fix first...
Regards

Zimmer[/QUOTE]

K I have read some in the link you send, I am gonna try figure it out, but i hope its the sound problem and not the graphic card. Well thanks for helping.

Regards Tobias

---

