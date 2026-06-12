---
title: "GAME CONQUEROR v2.0b -- a game cheating tool for Linux"
date: 2009-12-22
forum: Gaming &amp; Leisure
---

### Post by coolwanglu on 2009-12-22
Overview
--------

Cheat Engine is one of the most powerful cheating tool in Windows, as a experienced game cheater, I used it a lot and found it really handy. I've been always wondering why there's not a counterpart in Linux, and at last I decided to make one myself.

I dropped my early coded after I found scanmem, and decided to create a GUI front-end for it, called Game Conqueror. Thanks to Tavis (original author of scanmem), now GC is a part of scanmem.



Checkout
--------

[COLOR="Red"]
Updated 2010-01-05
Now a PPA for scanmem & gamemconqueror is avaiable:

[https://launchpad.net/~coolwanglu/+archive/scanmem](https://launchpad.net/~coolwanglu/+archive/scanmem)

Enjoy!
[/COLOR]


web page:
[http://code.google.com/p/scanmem/](http://code.google.com/p/scanmem/)

[COLOR="Red"]Updated: Now there is a v0.08 release, enjoy![/COLOR]

SVN Checkout:
svn checkout [http://scanmem.googlecode.com/svn/trunk/](http://scanmem.googlecode.com/svn/trunk/) scanmem

I had considered to created a PPA, but right now I don't that enough time for that, but packers will be welcomed.


Build
-----

You need automake, python and pygtk

./configure && make to build scanmem
and you can find the GameConqueror in gui/GameConqueror.py

You're recommend to execute the py file in a shell, because it is the only place you can see the error output and progress of scanning

Sorry for the inconvenience but so far GUI improvement has the lowest priority unless necessary. 


Usage
-----
You are assume to be familiar with CheatEngine, and you can see that the GUI is quite similar

Now all basic scan types (equal greater less increased(by) decreased(by) on all basic data types (int8/16/32/64 float8/16/32/64 or unknown width) have been implemented, you may found the easy-to-use syntax on the tooltip of 'Value:' label.

And for locking, you can only freeze a number but not make it 'not increased/decreased' as in CheatEngine, the delay is set to be 500ms, which could be changed in the .py file.


Support
-------

* Bug Report
  Please submit in the project page 

* Feature Request
  Actually there are still many features I'm working on, currently GameConqueror is just a simple basic tool. But all patches are welcomed

* Contribution
  If you like it, please provide some CODE instead of MONEY!



So that's all. Enjoy it!

---

### Post by Bölvaður on 2009-12-22
I dont get it... why would you cheat?

---

### Post by coolwanglu on 2009-12-22
> **Bölvaður said:**
> I dont get it... why would you cheat?
So I do know how to enjoy a game and I don't cheat very often.
But cheating could be fun, as some games are too hard, some are too boring, you can change the way it is
And cheating can also be necessary, when you want to play a game again without the savedata -- this always happens to me...

At least CheatEngine is amzing and I want a similar tool in Linux.

---

### Post by Clopin on 2009-12-22
Ah nice, been looking for something like this for a while.
Are you using ptrace() to edit & read memory?

---

### Post by coolwanglu on 2009-12-22
> **Clopin said:**
> Ah nice, been looking for something like this for a while.
Are you using ptrace() to edit & read memory?

/proc/<pid>/mem will be used if availabe, otherwise ptrace() will be used.

But in fact, currently these two ways are mixed up, and ptrace is used more often.

---

### Post by Sindwiller on 2009-12-23
Huh, that opens up a lot of technical exploits *besides* effin' cheating :/ I'd suggest you people should let your hands off this thing :P

Besides, every FOSS game has a debugging/cheating mode for, well, debugging/development purposes - which is also the case for almost every proprietary game, too. Why would you need a cheating tool?

> But cheating could be fun, ***as some games are too hard***, ***some are too boring***, you can change the way it is

I hope for your f* sake that you don't mean multiplayer games. :P

---

### Post by coolwanglu on 2009-12-23
> **Sindwiller said:**
> Huh, that opens up a lot of technical exploits *besides* effin' cheating :/ I'd suggest you people should let your hands off this thing :P

Besides, every FOSS game has a debugging/cheating mode for, well, debugging/development purposes - which is also the case for almost every proprietary game, too. Why would you need a cheating tool?



I hope for your f* sake that you don't mean multiplayer games. :P


Not every game has a debugging mode, like Flash games. Even there is, such kind of time is still useful. For boring games, or a boring part of a game, I have to find a way of passing it as fast as possible, after all you're playing the game, not the game playing you.

If I have to cheat the game, either I want to try the crazy mode, or the game itself sucks. I just want to have fun, and most of time I don't want to ruin the game by cheating.

For single player games, cheating means modifying but nothing, unless you upload your score or something like that. For multiplayer games, cheating is cheating, it should not be tolerated unless agreement ahead. When you play with others, the fun part is communication through the game, not only the game itself.

The tool itself is just a tool, I publish it only because it might be useful, but not to encourage cheating.

---

### Post by coolwanglu on 2009-12-24
I'm considering in implementation of memory viewer/editor, maybe ghex2 can be employed here...

---

### Post by Ryantoss on 2009-12-30
> **coolwanglu said:**
> I'm considering in implementation of memory viewer/editor, maybe ghex2 can be employed here...

Hello big man, you are my new hero for create this wonderful program. 

Just a simply problem, i am new for linux and whole thing. Currently i have Ubuntu 9.10 and got know idea to install your program.

What i did so far:

> Sudo apt-get install scanmem

> Sudo apt-get install python

I'm also find your python file in /Gui what am i suppose to do next. Just click in the link and it opens a long text file. How can i get that .py file. Looking for your reply soon.

Ryan Toss

---

### Post by coolwanglu on 2009-12-30
Hi, scanmem in the repository should not work, since I added more stuff in the latest version.

So here's what you should do:

1. checkout svn code
2. ```
sudo apt-get install automake python python-gtk2
```
3. ```
sudo apt-get build-dep scanmem
```
4. Enter the directory of the source code, and ```
./configure && make
```
5. Now you may execute it by execute ```
gui/GameConqueror.py
```

Hope this works.


> **Ryantoss said:**
> Hello big man, you are my new hero for create this wonderful program. 

Just a simply problem, i am new for linux and whole thing. Currently i have Ubuntu 9.10 and got know idea to install your program.

What i did so far:





I'm also find your python file in /Gui what am i suppose to do next. Just click in the link and it opens a long text file. How can i get that .py file. Looking for your reply soon.

Ryan Toss

---

### Post by Ryantoss on 2009-12-30
> **coolwanglu said:**
> Hi, scanmem in the repository should not work, since I added more stuff in the latest version.

So here's what you should do:

1. checkout svn code
2. ```
sudo apt-get install automake python python-gtk2
```
3. ```
sudo apt-get build-dep scanmem
```
4. Enter the directory of the source code, and ```
./configure && make
```
5. Now you may execute it by execute ```
gui/GameConqueror.py
```

Hope this works.

Sorry there, you lost me in enter the directory of source code. Where is the directory............ :lolflag: . Sorry for being a newbie question.

---

### Post by coolwanglu on 2009-12-30
> **Ryantoss said:**
> Sorry there, you lost me in enter the directory of source code. Where is the directory............ :lolflag: . Sorry for being a newbie question.

first you should checkout the source code

```
svn checkout http://scanmem.googlecode.com/svn/trunk/ scanmem
```

where the last parameter 'scanmem' is the name of the directory where you want to store the codes

then enter that directory

---

### Post by Ryantoss on 2009-12-30
> **coolwanglu said:**
> first you should checkout the source code

```
svn checkout http://scanmem.googlecode.com/svn/trunk/ scanmem
```

where the last parameter 'scanmem' is the name of the directory where you want to store the codes

then enter that directory

Man i lost completely from here 

> A    scanmem/configure
A    scanmem/Makefile.in
A    scanmem/commands.c
A    scanmem/scanmem.1
A    scanmem/commands.h
A    scanmem/depcomp
A    scanmem/licence.h
A    scanmem/configure.ac
A    scanmem/target_memory_info_array.c
A    scanmem/NEWS
A    scanmem/target_memory_info_array.h
A    scanmem/test
A    scanmem/test/smtest.c
A    scanmem/test/scanmem
A    scanmem/test/scanmem/version.exp
A    scanmem/test/scanmem/dregion.exp
A    scanmem/test/scanmem/shell.exp
A    scanmem/test/scanmem/testrun.log
A    scanmem/test/scanmem/testrun.sum
A    scanmem/test/scanmem/popchar.exp
A    scanmem/test/scanmem/iterchar.exp
A    scanmem/test/scanmem/lregions.exp
A    scanmem/test/config
A    scanmem/test/config/unix.exp
A    scanmem/test/smtest.dat
A    scanmem/maps.c
A    scanmem/handlers.c
A    scanmem/interrupt.h
A    scanmem/gui
A    scanmem/gui/GameConqueror_72x72.png
A    scanmem/gui/TODO
A    scanmem/gui/GameConqueror.xml
A    scanmem/gui/GameConqueror_128x128.png
A    scanmem/gui/README
A    scanmem/gui/GameConqueror.py
A    scanmem/menu.c
A    scanmem/maps.h
A    scanmem/handlers.h
A    scanmem/ChangeLog
A    scanmem/list.c
A    scanmem/README
A    scanmem/value.c
A    scanmem/ptrace.c
A    scanmem/config.h.in
A    scanmem/list.h
A    scanmem/value.h
A    scanmem/TODO
A    scanmem/main.c
A    scanmem/scanmem.h
A    scanmem/Makefile.am
A    scanmem/missing
A    scanmem/aclocal.m4
A    scanmem/install-sh
Checked out revision 31.
 

Could you please more detail. i do not know about directory command

---

### Post by coolwanglu on 2009-12-30
> **Ryantoss said:**
> Man i lost completely from here 

 

Could you please more detail. i do not know about directory command

cd scanmem

---

### Post by Ryantoss on 2009-12-30
> **coolwanglu said:**
> cd scanmem

It worked (i'm going to cry) god bless me one more experiences :popcorn:

I love it. BTW, could you please add the function freeze value next version. That is one of two most basic value of Cheatengine :P:guitar::lolflag:

---

### Post by coolwanglu on 2009-12-30
> **Ryantoss said:**
> It worked (i'm going to cry) god bless me one more experiences :popcorn:

Great

> **Ryantoss said:**
> I love it. BTW, could you please add the function freeze value next version. That is one of two most basic value of Cheatengine :P:guitar::lolflag:

What do you mean by 'function freeze value'? You mean freezing like 'not decrease'?

---

### Post by Ryantoss on 2009-12-30
> **coolwanglu said:**
> Great



What do you mean by 'function freeze value'? You mean freezing like 'not decrease'?

It mean freeze value. Make value no change at all. 

For example your character have 1000 HP, you do not want this amount lose anyway. Freeze HP and you are god :lolflag::lolflag:

---

### Post by coolwanglu on 2009-12-30
> **Ryantoss said:**
> It mean freeze value. Make value no change at all. 

For example your character have 1000 HP, you do not want this amount lose anyway. Freeze HP and you are god :lolflag::lolflag:

It's already there...

---

### Post by Ryantoss on 2009-12-30
> **coolwanglu said:**
> It's already there...

Some of basic function i can think of, some question as well man. Sorry for did not see this freeze first time. :lolflag: 

1. What make the different when cheatengine is fast scanning while scanmem is much slower.

2. I'm going to make a command like this. For just click one time rather than open terminal.

> cd scanmem gui/GameConqueror.py

Will this command work. I got no luck at all.

3. Is it possible for build in terminal process within GUI. Mean that scanning process will show their scanning inside display of GUI rather than in terminal.

4. Save, load......... man :D it's going to be cheat engine. I'm get excited :guitar:

---

### Post by coolwanglu on 2009-12-30
> **Ryantoss said:**
> Some of basic function i can think of, some question as well man. Sorry for did not see this freeze first time. :lolflag: 

1. What make the different when cheatengine is fast scanning while scanmem is much slower.

2. I'm going to make a command like this. For just click one time rather than open terminal.



Will this command work. I got no luck at all.

3. Is it possible for build in terminal process within GUI. Mean that scanning process will show their scanning inside display of GUI rather than in terminal.

4. Save, load......... man :D it's going to be cheat engine. I'm get excited :guitar:

1. It's the problem of the design of scanmem, I'll work on them
2. Currently user-friendly things are at the lowest priority, sorry for this. Right now I'm the only one maintaining this, I don't have enough time. And I'll focus on functions instead of user interfaces.
3. I'm considering in creating a progress bar for this
4. See #2

---

### Post by Ryantoss on 2009-12-30
> **coolwanglu said:**
> 1. It's the problem of the design of scanmem, I'll work on them
2. Currently user-friendly things are at the lowest priority, sorry for this. Right now I'm the only one maintaining this, I don't have enough time. And I'll focus on functions instead of user interfaces.
3. I'm considering in creating a progress bar for this
4. See #2

For #2 i just mean that i'm going to create a custome application launcher. It helps me to one click to open gameconqueror rather than open terminal and ty two times ==> three steps. A custom application launcher reduce this to one step.

I got not luck with my current command. Could you help me out :(

---

### Post by coolwanglu on 2009-12-30
> **Ryantoss said:**
> For #2 i just mean that i'm going to create a custome application launcher. It helps me to one click to open gameconqueror rather than open terminal and ty two times ==> three steps. A custom application launcher reduce this to one step.

I got not luck with my current command. Could you help me out :(

[http://blogs.techrepublic.com.com/howdoi/?p=193](http://blogs.techrepublic.com.com/howdoi/?p=193)

btw, you should learn to use Google

---

### Post by coolwanglu on 2009-12-31
Now I've released a v0.08 version for convenience, enjoy!

---

### Post by VastOne on 2009-12-31
> **coolwanglu said:**
> [http://blogs.techrepublic.com.com/howdoi/?p=193](http://blogs.techrepublic.com.com/howdoi/?p=193)

btw, you should learn to use Google

Dude, your patience is amazing

Impressive

---

### Post by Ryantoss on 2010-01-02
> **VastOne said:**
> Dude, your patience is amazing

Impressive

What i have to say T_T

1. Firstly i'm new for Linux (two weeks) and i did not know where default install directory. How can i make such command to work since i got no correct directory.

2. Secondly, coder might not be gamer. Gamer might not be coder. I'm a regular gamer ,i make request and suggesting, that's all. 

However, patience is good ^^:)

---

### Post by coolwanglu on 2010-01-02
> **Ryantoss said:**
> What i have to say T_T

1. Firstly i'm new for Linux (two weeks) and i did not know where default install directory. How can i make such command to work since i got no correct directory.

2. Secondly, coder might not be gamer. Gamer might not be coder. I'm a regular gamer ,i make request and suggesting, that's all. 

However, patience is good ^^:)

Currently the gui part is not installed to nowhere, I'll fix this and add a menu item or something.

Right now, you may create a launcher, and locate to where you expanded the source code tarball, and then the `gui' directory, where you can find GameConqueror.py

---

### Post by coolwanglu on 2010-01-04
Now a ppa is avaiable, article updated.

---

### Post by coolwanglu on 2010-01-07
Now all basic scans for numbers have been implemented

I mean (equalto greaterthan lessthan increased decreased increasedby decreasedby) on (integer and float)

You may use the ppa or latest code in svn.

Please have a try and let me know if it works.

---

### Post by Epim3theus on 2010-05-06
I looked at all the posts and I got to sudo apt-get install automake python python-gtk2. Then it asked for a password. I know this is a unintelligent question to ask, but I am only 15 and it is my first day on Linux. Can someone help?

---

### Post by coolwanglu on 2010-05-07
> **Epim3theus said:**
> I looked at all the posts and I got to sudo apt-get install automake python python-gtk2. Then it asked for a password. I know this is a unintelligent question to ask, but I am only 15 and it is my first day on Linux. Can someone help?

You need to provide the password of your UBUNTU ACCOUNT

---

### Post by prkahrvat on 2011-11-14
Hello coolwanglu and thank you for this nice remake of scanmem which needed upgrade. I'm using gc alot already and having same problem from the beginning. If i turn out browser ( i cheat on flash game mostly ) before gc, gc stay blocked. I tried to kill process on every kind of way but it impossible without restarting pc. is there any way to fix it?

Thank you, and sorry for my lousy english!

---

### Post by coolwanglu on 2011-11-17
This should have already been fixed in the latest version

Please update from 
[https://launchpad.net/~coolwanglu/+archive/scanmem](https://launchpad.net/~coolwanglu/+archive/scanmem)
or
[http://code.google.com/p/scanmem](http://code.google.com/p/scanmem)

---

### Post by erikthedrink on 2012-03-14
I tried using Game Conqueror on a game called Monster RPG2. I found the pid for the process. Yet it reads, "Failed to attach to 3809, Operation not permitted" What else do I need to do?:confused: Oops, didn't sudo gameconqueror. works now.

---

### Post by coolwanglu on 2012-03-15
> **erikthedrink said:**
> I tried using Game Conqueror on a game called Monster RPG2. I found the pid for the process. Yet it reads, "Failed to attach to 3809, Operation not permitted" What else do I need to do?:confused: Oops, didn't sudo gameconqueror. works now.

First make sure you are using the latest version.

GC should ask you for root privilege, if not, please run GC as root.

---

### Post by erikthedrink on 2012-04-07
I upgraded Gameconqueror to version 0.12. I thought I had modified scanmem to version 0.12, yet now Gameconqueror, version 0.12 is telling me I do not have a matching scanmem version.:confused:

---

### Post by erikthedrink on 2012-04-07
This is how the error screen in GameConqueror 0.12 reads:
Version of scanmem mismatched, you may encounter problems. Please make sure you are using the same version of Gamconqueror as scanmem.):P

---

### Post by coolwanglu on 2012-04-07
> **erikthedrink said:**
> This is how the error screen in GameConqueror 0.12 reads:
Version of scanmem mismatched, you may encounter problems. Please make sure you are using the same version of Gamconqueror as scanmem.):P

can you please try the latest version in the PPA?

---

### Post by erikthedrink on 2012-04-07
Thanks, Cool Wang Lu! I got it from the PPA. I had to un-install the old scanmem first.:guitar:

---

### Post by zarg@henrikke on 2012-07-10
Followed the instructions...

```

$ sudo apt-get install automake python python-gtk2
$ svn checkout http://scanmem.googlecode.com/svn/trunk/ scanmem
$ sudo apt-get build-dep scanmem
$ cd scanmem/
$ ./configure && make
$ gui/GameConqueror.py
Traceback (most recent call last):
  File "gui/GameConqueror.py", line 36, in <module>
    from consts import *
ImportError: No module named consts
$ python -V
Python 2.7.1+

```

not familiar with python, could the 'consts import *' failure be related to a problem with the python build?

---- EDIT ---

OK, tried this instead
```

$ wget http://scanmem.googlecode.com/files/scanmem-0.12.tar.gz
$ tar zxvf scanmem-0.12.tar.gz
$ ./configure && make
$ gui/GameConqueror.py

```

and GC started, yess!

---

### Post by SandJ on 2012-12-06
I started reverse engineering games to [s]cheat[/s] *extend their playability* once I had got bored of playing them straight back in the early 1980s.  Thus began my career in computer programming.  These days I'm too busy to write my own utilities.

> **coolwanglu said:**
> ... I found scanmem, and decided to create a GUI front-end for it, called Game Conqueror.You're a hero, dude.  Ta muchly.

---

### Post by Xarin on 2012-12-15
> **zarg@henrikke said:**
> Followed the instructions...

```

$ sudo apt-get install automake python python-gtk2
$ svn checkout http://scanmem.googlecode.com/svn/trunk/ scanmem
$ sudo apt-get build-dep scanmem
$ cd scanmem/
$ ./configure && make
$ gui/GameConqueror.py
Traceback (most recent call last):
  File "gui/GameConqueror.py", line 36, in <module>
    from consts import *
ImportError: No module named consts
$ python -V
Python 2.7.1+

```

not familiar with python, could the 'consts import *' failure be related to a problem with the python build?

---- EDIT ---

OK, tried this instead
```

$ wget http://scanmem.googlecode.com/files/scanmem-0.12.tar.gz
$ tar zxvf scanmem-0.12.tar.gz
$ ./configure && make
$ gui/GameConqueror.py

```

and GC started, yess!

tried both of these the first gives me this error:
```

"Traceback (most recent call last):
  File "./GameConqueror.py", line 36, in <module>
    from consts import *
ImportError: No module named consts" 

```

and then the second gives me this error:
```

"Traceback (most recent call last):
  File "./GameConqueror.py", line 930, in <module>
    GameConqueror().main()
  File "./GameConqueror.py", line 297, in __init__
    self.backend = GameConquerorBackend()
  File "/home/username/Programs/scanmem-0.12/gui/backend.py", line 38, in __init__
    self.restart()
  File "/home/username/Programs/scanmem-0.12/gui/backend.py", line 51, in restart
    self.backend = subprocess.Popen(BACKEND, stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=self.stderrfile.fileno())
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1259, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory"

```
Any help would be greatly appreciated thanks!

---

### Post by SandJ on 2012-12-15
> **Xarin said:**
> Any help would be greatly appreciated thanks!Rather than compiling it, have you tried the PPA?   Worked first time for me on my Xubuntu 12.04 system:

> **coolwanglu said:**
> [COLOR=Red]Now a PPA for scanmem & gamemconqueror is available:

[https://launchpad.net/~coolwanglu/+archive/scanmem]("https://launchpad.net/%7Ecoolwanglu/+archive/scanmem")[/COLOR]I just added 
```
deb [http://ppa.launchpad.net/coolwanglu/scanmem/ubuntu](http://ppa.launchpad.net/coolwanglu/scanmem/ubuntu) precise main
```  (where 'precise' is only valid for v12.04 of course)  to the software sources in the Ubuntu Software Centre and Game Conqueror became available for installation.

---

### Post by Xarin on 2012-12-15
> **SandJ said:**
> Rather than compiling it, have you tried the PPA?   Worked first time for me on my Xubuntu 12.04 system:

I just added 
```
deb [http://ppa.launchpad.net/coolwanglu/scanmem/ubuntu](http://ppa.launchpad.net/coolwanglu/scanmem/ubuntu) precise main
```  (where 'precise' is only valid for v12.04 of course)  to the software sources in the Ubuntu Software Centre and Game Conqueror became available for installation.

Cool that got it working, thanks!

---

