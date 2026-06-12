---
title: "how to install a good chess game ?"
date: 2006-10-31
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2006-10-31
I'm looking for a good chess game
I've tried to install a few but with no luck
I understand that there is a GUI and an engine but I don't know how to install them both.

can you pick a good and stable chess game and pose a step-by-step how to install it and were to get it from under edgy ?

p.s
I'm looking for a single player chess game with an option for multi-player
but single player is a must.

thanks.

---

### Post by xpod on 2006-10-31
pouetchess looks good.
Ive installed it from synaptic but not actually played it yet.

---

### Post by MaximB on 2006-11-01
help ?

---

### Post by whiterabbit on 2006-11-01
$sudo apt-get install gnome-chess gnuchess
$gnome-chess

Settings -> Preferences -> Programs -> Add -> Enter a name and location*

*i.e. /usr/games/gnuchess

Click apply and ok.  Select [name of given program] under File -> Programs.

Then you're ready to go.

---

### Post by whiterabbit on 2006-11-01
Oh, I also recommend $sudo aptitude install brutalchess

It's the one I use.

---

### Post by MaximB on 2006-11-01
I've lost you right about here :
"Settings -> Preferences -> Programs -> Add -> Enter a name and location*

*i.e. /usr/games/gnuchess

Click apply and ok. Select [name of given program] under File -> Programs."

I don't see "programs" in the system>preferences tab
were is it ?

---

### Post by whiterabbit on 2006-11-01
Not systems -> preferences.... *settings* -> preferences.  In the game, not in gnome.

It's the tab on the right, up the top.

I still recommend brutalchess for single player.

---

### Post by Perfect Storm on 2006-11-01
Here's a good one I like: [http://doc.gwos.org/index.php/GlChess](http://doc.gwos.org/index.php/GlChess)
It have both single and multiplayer option.

---

### Post by whiterabbit on 2006-11-01
> **Artificial Intelligence said:**
> Here's a good one I like: [http://doc.gwos.org/index.php/GlChess](http://doc.gwos.org/index.php/GlChess)
It have both single and multiplayer option.
Just had a go.  I like it, thanks.

---

### Post by MaximB on 2006-11-01
you know what my main problem with installing games/programs like that ?
I need to memorize them as there are no short cuts in the "applications" menu.

---

### Post by whiterabbit on 2006-11-01
> **MAXDDARK said:**
> you know what my main problem with installing games/programs like that ?
I need to memorize them as there are no short cuts in the "applications" menu.You can add any program to the menu by...

right click applications > edit menus > (for example)click games > click new item > enter details and location > enjoy. :)

---

### Post by MaximB on 2006-11-01
yeah...but were are those programs ? were does it get installed with apt-get ?

---

### Post by whiterabbit on 2006-11-01
Well in the case of games, they usually get intalled in /usr/games/

---

### Post by whiterabbit on 2006-11-01
Give this a read aswell....

[http://monkeyblog.org/ubuntu/installing/#where_did_it_go](http://monkeyblog.org/ubuntu/installing/#where_did_it_go)

---

### Post by Perfect Storm on 2006-11-01
Uasually just type the name of the game/applications in the terminal do the trick, just remember to use low case letters.

---

### Post by MaximB on 2006-11-01
yeah, thanks
and A-I : your Linux game sites are good
and if you have not added this game yet I really recommand it
it's the best RTS ever made IMHO.

Total annihilation spring

[http://taspring.clan-sy.com/](http://taspring.clan-sy.com/)
here's the ubuntu/debian easy-install :
[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring)

it's like the game in your site but with more maps, more mods, free, open source, runs on Linux, and YOU DON'T NEED THE OLD GAME TO RUN IT.

---

### Post by Perfect Storm on 2006-11-01
Already have it, thanks anyway :KS 
Any tips, news etc. are welcome.

---

### Post by UbuWu on 2006-11-01
[PyChess]("http://pychess.googlepages.com/")

Has a builtin chess engine, and you can install others if you like. Is undergoing some rapid development and is looking very nice. However no ubuntu packages yet, but as it is a python program, you can just unpack it and run it.

---

### Post by MaximB on 2006-11-02
how do I run this game ? tried running setup.py and PyChess.py but nothing happen

---

### Post by whiterabbit on 2006-11-02
To run a .py file, you need to make it executable...

```
chmod +x PyChess.py
``` and execute it by running ./PyChess.py

...or just put the word python in front of it...

```
python PyChess.py
```

---

### Post by MaximB on 2006-11-02
maxim@maxim:~/maxddark/games/pychess$ python PyChess.py
Traceback (most recent call last):
  File "PyChess.py", line 15, in ?
    from Players import engines
  File "/home/maxim/maxddark/games/pychess/Players/engines.py", line 31, in ?
    from PyChess import PyChessEngine
  File "/home/maxim/maxddark/games/pychess/Players/PyChess.py", line 9, in ?
    from Utils.book import getOpenings
  File "/home/maxim/maxddark/games/pychess/Utils/book.py", line 3, in ?
    from System import tsqlite
  File "/home/maxim/maxddark/games/pychess/System/tsqlite.py", line 1, in ?
    import pysqlite2.dbapi2 as sqlite
ImportError: No module named pysqlite2.dbapi2

---

### Post by whiterabbit on 2006-11-02
So there are files missing or the code is fudged.

---

### Post by Perfect Storm on 2006-11-03
```
sudo aptitude install python-sqlite
```

python interface to SQLite 3 is installed by default but not python interface to SQLite 2. Perhaps it wants version 2 and not 3. It's a worth to try.

---

### Post by MaximB on 2006-11-03
still the same problem

maxim@maxim:~/maxddark/games/pychess$ python PyChess.py
Traceback (most recent call last):
  File "PyChess.py", line 15, in ?
    from Players import engines
  File "/home/maxim/maxddark/games/pychess/Players/engines.py", line 31, in ?
    from PyChess import PyChessEngine
  File "/home/maxim/maxddark/games/pychess/Players/PyChess.py", line 9, in ?
    from Utils.book import getOpenings
  File "/home/maxim/maxddark/games/pychess/Utils/book.py", line 3, in ?
    from System import tsqlite
  File "/home/maxim/maxddark/games/pychess/System/tsqlite.py", line 1, in ?
    import pysqlite2.dbapi2 as sqlite
ImportError: No module named pysqlite2.dbapi2


but no worries - those other chess games are great.
ubuntu should have included them and not that buggie crashing game...

---

### Post by UbuWu on 2006-11-03
> **Artificial Intelligence said:**
> ```
sudo aptitude install python-sqlite
```

python interface to SQLite 3 is installed by default but not python interface to SQLite 2. Perhaps it wants version 2 and not 3. It's a worth to try.

You need **python-sqlite2**

---

### Post by MaximB on 2006-11-03
maxim@maxim:~$ sudo aptitude install python-sqlite2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "python-sqlite2"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used

---

### Post by Lobais on 2006-11-03
It seems that the ubuntu package name is python2.4-pysqlite2 as in [http://packages.ubuntulinux.org/dapper/python/python2.4-pysqlite2](http://packages.ubuntulinux.org/dapper/python/python2.4-pysqlite2)

---

### Post by MaximB on 2006-11-03
all working great now...thanks.
all but the chess game that was brought into ubuntu repros, that one suck big time.

---

### Post by Lobais on 2006-11-03
Yeah, the gnome-chess one? It also hasn't been worked on since 06/01/2001

---

### Post by MaximB on 2006-11-03
actually I've ment pouetChess - the 3d one that always crashes.

---

### Post by whiterabbit on 2006-11-03
Yep, pouetChess crashes for me everytime.

Have you tried brutalchess yet?  It's great for single player and it's pretty.

---

### Post by UbuWu on 2006-11-03
> **Lobais said:**
> It seems that the ubuntu package name is python2.4-pysqlite2 as in [http://packages.ubuntulinux.org/dapper/python/python2.4-pysqlite2](http://packages.ubuntulinux.org/dapper/python/python2.4-pysqlite2)

To make the confusion complete: On dapper it is python2.4-pysqlite2 and on edgy it is python-pysqlite2 ](*,)

---

