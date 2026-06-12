---
title: "How do you play the fruit chess engine with a gui (xboard, eboard, etc)?"
date: 2007-10-16
forum: Gaming &amp; Leisure
---

### Post by cinematography on 2007-10-16
When I installed the crafty chess engine, the eboard, pychess, and knights graphical user interfaces all found it and automatically added it as an option. Woot. But when I installed other engines, they are no where to be found in the menus.

xboard has an option for using other engines: 
```
xboard -fcp "./crafty" -fd /usr/games/crafty
```

But, for some reason, it just doesn't work. 

I get this error: 
```
xboard: Error writing to first chess program: Broken pipe
xboard: Error: first chess program (./crafty) exited unexpectedly
xboard: Error writing to first chess program: Broken pipe
```


Any help on how I can play these other engines would be greatly appreciated.

---

### Post by elj4176 on 2007-10-16
I think its a difference in the engine protocols. Crafty is wb and fruit is UCI. There is a connector called polygot but I haven't tried it yet.
You could also try running arena with wine.

---

### Post by cinematography on 2007-10-16
> **elj4176 said:**
> I think its a difference in the engine protocols. Crafty is wb and fruit is UCI. There is a connector called polygot but I haven't tried it yet.
You could also try running arena with wine.
Arena with wine is the way. :) Thank you.

---

### Post by Lobais on 2007-11-28
You might want to download the new version of PyChess - Philidor. It is not yet in the ubuntu repositories, but you get grab a deb from   [http://www.getdeb.net/app.php?name=PyChess](http://www.getdeb.net/app.php?name=PyChess) or [http://gnomefiles.org/app.php/PyChess](http://gnomefiles.org/app.php/PyChess)

It has support for the UCI engines, and should automatically locate engines like Fruit, Glaurung and Shredder.

---

### Post by aasdfasdfg on 2010-01-06
You have a mistake, in the -fd path you need to specify the folder, not the file.
/usr/games instead of /usr/games/crafty

---

