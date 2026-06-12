---
title: "Creating a 1:1 perfect image"
date: 2007-05-06
forum: Gaming &amp; Leisure
---

### Post by Rizado on 2007-05-06
I'm posting this here because it's about getting a game to work perfectly, but to be honest it has little to do with gaming. It's just that I found no other place to post it.

I got Warcraft III Frozen Throne working perfectly, bnet and everything. There's just one thing, wc3 requires the cd to work. This is starting to get really annoying with all the noise now and then and it's also taking one of my drives. Have tried some cracks but they don't work, probably because it uses memory hooks or something I don't really remember, also I don't really like the idea of using cracks on a bought online game...
So my thought is to create a image of the cd and keep it on a drive always mounted. This way Wc3 will do it's checks and everything will be fine and quiet. The big question is, how do I do this? Have tried to make a iso using "dd bs=2048 if=/dev/hdc of=/home/blahblah/wc3.iso" and mounting it. However this does not work. Probably because the place that needs to be read does not exist?

Any ideas how to make a working image? I don't care about beeing able to burn it again, and if posible it should be small.

EDIT: I never figured out how to make a 1:1 copy but I did figure out a way to play without a cd. Read more [_further down the page._](http://ubuntuforums.org/showthread.php?p=2616356#post2616356)

---

### Post by dummies85 on 2007-05-06
you can try using cd emulator program, i found [CDemu]("http://cdemu.sourceforge.net/")

but usually the game itself have some sort of protection that can detect emulation program, that happens on windows

---

### Post by Breepee on 2007-05-06
You could try to use an image from the grey parts of the web. Mostly the clones you find there are ripped with the right equipment and method so that the game registers it as the real disc. Or perhaps there's a crack for your game? I pretty much always use those, because I too hate swapping discs all the time.

---

### Post by psusi on 2007-05-06
What "didn't work" and why?  Did it fail to mount?  If so what was the exact command and error message?  Did the game claim it can't find the cd?  Most likely the game actually wants to do some low level messing around with intentionally damaged portions of the disc, which doesn't work on an image file.

---

### Post by Rizado on 2007-05-08
> **psusi said:**
> What "didn't work" and why?  Did it fail to mount?  If so what was the exact command and error message?  Did the game claim it can't find the cd?  Most likely the game actually wants to do some low level messing around with intentionally damaged portions of the disc, which doesn't work on an image file.Exactly, Warcraft uses securom 4.8 or 5 or something I think and I've read somewhere that is what it does (Something about subchannel Q and W maybe). An iso won't use copy those channels, and a bin probably wont work either.

The cracks I've found for WC3 are loaders that uses APIHooks, which doesn't work very well in wine.

Anyway I found something quite interesting out while looking at a loader script. If you start the game with a cracked exe and then replace it with a original there's no trouble using battlenet :) I'm gonna write myself a little script.

---

### Post by Sukarn on 2007-05-08
Don't forget to post the script here when you're done with it.

---

### Post by Rizado on 2007-05-08
> **Sukarn said:**
> Don't forget to post the script here when you're done with it.Nope :D I'm gonna post it right now!

Okey so I found a Diablo 2 loader script that were supposed to allow play on bnet with a crack but it was pretty bloated imo and I never got it to work. Anyway I figured out that what it was doing was starting the game with a fixed exe and after some time it replaced it with the original one. Tried that and it worked!

So I've come up with a script that probably isn't as faulty proof as the one I found but much easier to understand and it's working. Just be sure you READ THE INSTRUCTIONS CAREFULLY FIRST or you'll end up with missing exe files. Not the end of the world but pretty damn annoying.

```
#!/bin/bash

# MAKE SURE YOU KEEP A BACKUP OF YOUR EXE FILES IN CASE ANYTHING GOES WRONG.
# NAME THE ORIGINAL EXE war3.exe AND THE FIXED war3.fxd


# EDIT LINES BELOW
WC3PATH="/path/to/Warcraft III"
WAR3ORG="war3.org"
WAR3FIXED="war3.fxd"

# UNCOMMENT LINE BELOW IF YOU HAVE FROZEN THRONE AND WANT TO PLAY REIGN OF CHAOS
# ROC="-classic"

# EDIT BELOW ONLY IF YOU NEED, GAME IS RUN WITH WINE DEBUG OFF AND IN OPENGL MODE.
# THE SCRIPT ALSO TAKES COMMANDLINE ARGUMENTS LIKE: war3script -window

cd "$WC3PATH"

if [ -e "war3.exe" ];
then
    rm "war3.exe"
fi

cp "$WAR3FIXED" "war3.exe"

echo
echo "Starting Game..."
echo

WINEDEBUG="-all" wine "war3.exe" "$ROC" -opengl "$@" &
sleep 5 # TIME IN SECONDS BEFORE REPLACING FIXED EXE WITH ORIGINAL ONE.

echo
echo "Replacing fixed exe with original one..."
echo

rm "war3.exe"
cp "$WAR3ORG" "war3.exe"
```

Copy this script into a file in the Warcraft III directory. If you have Frozen Throne you might want to have two copies with ROC enabled in one of them. I have named them war3tft and war3roc. Edit the scripts and read the instructions in there. What you need to do is edit WC3PATH="". You also need to rename the original war3.exe in your game directory to war3.org and name the fixed one war3.fxd. MAKE BACKUPS!!!

Make the scripts executable, can be done by ```
chmod +x war3tft war3roc
``` and get ready to run without a cd!

To play Reign of Chaos with Frozen Throne installed you'll need to uncomment
# ROC="-classic

Note that you'll have to have a fixed(cracked) and working exe before this script will work. Also:
THIS WILL NOT ALLOW YOU TO PLAY ON BNET WITHOUT A BOUGHT GAME. You'll still need a valid cd key.

I'll be happy to answer any questions, but please carefully read the instructions first!

---

### Post by Rizado on 2007-05-09
Is it possible to change the title of a topic? I've edited the first message but it doesn't change the topic name.

---

