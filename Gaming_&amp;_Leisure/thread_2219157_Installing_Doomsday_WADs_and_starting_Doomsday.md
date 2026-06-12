---
title: "Installing Doomsday WADs and starting Doomsday?"
date: 2014-04-23
forum: Gaming &amp; Leisure
---

### Post by CybaCowboy on 2014-04-23
All right, a nice easy one for you all...


I installed "Doomsday" from the Ubuntu Software Center, but where do I put my Doom WAD files?


Also, the Ubuntu Software Center says that I need to run this from Terminal - what is the applicable command and is it possible to create a shortcut in the Unity applications/programs menu to run Doomsday?

-

[I]This question was also cross-posted on AskUbuntu here:
[http://askubuntu.com/questions/452735/installing-doomsday-wads-and-starting-doomsday](http://askubuntu.com/questions/452735/installing-doomsday-wads-and-starting-doomsday)[/I]

---

### Post by King Dude on 2014-04-23
First you must locate your Doom/Doom2/Final Doom/Ultimate Doom WAD files, and when you install Doomsday it should ask you to select the games you own and to select the WAD files for them. You could also try clicking the "+" at the bottom of the left-hand window when you launch the program.

---

### Post by CybaCowboy on 2014-04-23
> **King Dude said:**
> First you must locate your Doom/Doom2/Final Doom/Ultimate Doom WAD files

In a compressed folder, in my "Download" folder...


> **King Dude said:**
> and when you install Doomsday it should ask you to select the games you own and to select the WAD files for them.

I installed the version from the Ubuntu Software Center, which did not ask where the WAD files were on installation...


> **King Dude said:**
> You could also try clicking the "+" at the bottom of the left-hand window when you launch the program.

The Ubuntu Software Center indicates that I must start this from the Terminal (hence the part of my question relating to whether or not I can add a Unity menu shortcut) with the command "doomsday", however when I try to do so, I am told:
```
loadGamePlugin: No game library was specified.Z_Shutdown: Used 0 volumes, total 0 bytes.
```

I'm not too sure what "+" you are referring to...

---

### Post by mastablasta on 2014-04-24
i am not sure if i remember correctly, but i believe there should be a (hidden) folder ./doomsday in home folder and you put the files somewhere inside that folder. this i need to check at home to verify.

you are correct that the one in software center is ran from terminal. i was a bit dissapointed. in windows Kicks makes it easy to run&configure doom engine games, runs with openGL 3D models out of the box, with various openGL effects... while here all i get it 2D sprites. it works but it's a distant echo compared to kicks on windows. i've been trying to find similar launcher to kicks in linux but so far doesn't seem like it exists.

terminal to launch games.... i mean really. is this dos era? :-P at least it could create a shortcut.

---

### Post by CybaCowboy on 2014-04-25
> **mastablasta said:**
> i am not sure if i remember correctly, but i believe there should be a (hidden) folder ./doomsday in home folder and you put the files somewhere inside that folder. this i need to check at home to verify.


I couldn't see a "./doomsday" folder in the Home folder, nor any *clear* sign of where the WADs *should* be placed... In saying this, I *did* find an interesting list of directories, called "doomsday.list".

Here's what's in the file:
[I]/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/doomsday
/usr/share/doc/doomsday/dhistory.txt.gz
/usr/share/doc/doomsday/copyright
/usr/share/doc/doomsday/network.txt.gz
/usr/share/doc/doomsday/changelog.Debian.gz
/usr/share/deng
/usr/share/deng/data
/usr/share/deng/data/jdoom
/usr/share/deng/data/jdoom/jdoom.pk3
/usr/share/deng/data/jheretic
/usr/share/deng/data/jheretic/jheretic.pk3
/usr/share/deng/data/jhexen
/usr/share/deng/data/jhexen/jhexen.pk3
/usr/share/deng/data/doomsday.pk3
/usr/share/man
/usr/share/man/man6
/usr/share/man/man6/doomsday.6.gz
/usr/lib
/usr/lib/deng
/usr/lib/deng/libjhexen.so
/usr/lib/deng/libdpwadmapconverter.so
/usr/lib/deng/libjheretic.so
/usr/lib/deng/libjdoom.so
/usr/lib/deng/libdpdehread.so
/usr/games
/usr/games/doomsday[/I]

Is *this* any help with relation to *where* the WAD files should be placed?


> **mastablasta said:**
> you are correct that the one in software center is ran from terminal. i was a bit dissapointed. in windows Kicks makes it easy to run&configure doom engine games, runs with openGL 3D models out of the box, with various openGL effects... while here all i get it 2D sprites. it works but it's a distant echo compared to kicks on windows. i've been trying to find similar launcher to kicks in linux but so far doesn't seem like it exists.

terminal to launch games.... i mean really. is this dos era? :-P at least it could create a shortcut.

I don't mind the 2D sprites... I was gaming when this was "new", so for me it gives that "retro" feeling to the game (in saying that, the enhanced "Megaton Edition" of Duke Nukem 3D *does* look pretty good under Steam for Linux!).

However, the Terminal thing is just a pain... Terminal is more efficient (and in *some* cases, faster!) for many things - launching games is _not_ one of them.

*Surely* there's gotta be a way to add a Unity shortcut to a Terminal command though, right?

---

### Post by mastablasta on 2014-04-26
ah found it... it actually doesn't matter where you have the wad files as you can point to them in command line:
[http://ubuntuforums.org/showthread.php?t=1588867](http://ubuntuforums.org/showthread.php?t=1588867)

e.g.: ```
/usr/games/doomsday  -game jdoom -file /home/user/jdoom/doom2.wad
```

if wads are in user's home in jdoom folder (edit: probably you do not need the whole path to doomsday, i don't know why i put it there...).

lame though that one needs to use command line to launch it.

oh and the openGL 3D monster are super cool and really bring new life to this game.
though i am not sure if they are available for heretic and hexen. also hexen multiplayer (not sure if they fixed it already) weapons are missing for the other player that is not running server.

now, go get those aliens!

---

