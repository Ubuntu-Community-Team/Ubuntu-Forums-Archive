---
title: "my ubuntu is in trouble, something is wrong"
date: 2009-03-02
forum: General Help
---

### Post by aykut.karaca on 2009-03-02
Hi there, I am a beginner...I installed ubuntu 6 months ago and I absolutely didnt have any problems till this weekend I installed wolfeinstein game for ubuntu...I think all started after that. I even played the game. I turned the computer off and next day when I turned on again, ubuntu started and everything was normal.

The programs on the desktop are accessible and run, although I think unstable, but I dont see the menubar. There is the bar but no menus. sometimes the menus come but I cant click on them. 

I can right click on the desktop but when I choose any item. ubuntu hangs. Also I cant see other data partition in normal I was able to see.

I dont know whatelse to say. I can start terminals by pressing ctrl+alt+f1 etc and see the content of my ubuntu primary partition. 

If you help me I will try to give more information by running commands.

I am sure something I installed for the game clashed with gnome or something like that...

---

### Post by sandyd on 2009-03-02
it would be nice if you posted this in the 

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)
instead

have you tried removing the game?

run this for me while you figure out how to remove it.....
```

lspci

```

---

### Post by emojay on 2009-03-02
I think, you should check your pc specs if the it is compatible with the game, and try removing the game first and see what will happen?

---

### Post by Roanoke on 2009-03-02
Did you install the game through synaptic or through apt-get? If you did, then open synaptic again and uninstall it (or, even better, press ALT+F2, type in 'terminal', hit enter, and type in this in the window:
```
sudo apt-get purge wolfenstein
```
and press enter)

---

### Post by aykut.karaca on 2009-03-03
well I am really newby :)

how can I see the list of softwares installed? as I dont know how to uninstall. Its name is not wolfenstein.

I remember I ran this before I install:

sudo apt-get install libgtk1.2 

actually I followed all the steps in the page :
[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

so I need to revert all those things, I think.

Can this make the op system that unstable? what do you think?

---

### Post by aykut.karaca on 2009-03-03
Guys thanks for everything...I solved my problem!

I uninstalled libgtk and esound and it worked! definetely something was clashing...

I have my lovely ubuntu now! I dont need Windows anymore!

---

### Post by emojay on 2009-07-07
Good for you. congrats. i'm also changing to ubuntu

---

