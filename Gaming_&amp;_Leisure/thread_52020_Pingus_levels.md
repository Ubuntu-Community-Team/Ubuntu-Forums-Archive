---
title: "Pingus levels"
date: 2005-07-26
forum: Gaming &amp; Leisure
---

### Post by Nonno Bassotto on 2005-07-26
Is there any pingus player out there? I've just finished the tutorial island levels and I was quite surprised to see that this was the end. Then I found lots of levels in the folder /usr/share/games/pingus/levels, and some worldmaps too in /usr/share/games/pingus/worldmaps. Still I don't know how to play them, other than in  editing mode, which is quite tedious. Any way to include the levels in the game?
Thank you
Andrea

---

### Post by skirkpatrick on 2005-07-26
I've been trying to figure this out for my daughter.  So far, no success.

---

### Post by charlieg on 2005-07-26
There are more levels available.  You'll probably have to trawl through the pingus-devel mailing list archives to find them though.

The problem is there's nobody working on Pingus at the moment.  It just needs a little kick to update it to the latest clanlib and package some extra levels.

---

### Post by Nonno Bassotto on 2005-07-28
Ok,a decent way to do this is by typing

pingus /usr/share/games/pingus/levels/somefolder/somelevel.xml

where for somefolder I recommend "playable". This can be annoying because you have to play separately each level. So you may try also

pingus --worldmap /usr/share/games/pingus/worldmaps/someworldmap.xml

which lets you play a worldmap. I hope those are really playable. Surely they lack some features like levels names and comments. I've found no way to actually include these levels into the game.
Andrea

---

### Post by cartisdm on 2007-11-22
I'm really curious about this as well.  I finished up the tutorial levels in a hurry to get to the actual game then only to find out thats it!  Is 0.7.1 the newest version, there's no add-on levels to download?

---

### Post by kmullinax on 2008-02-10
I pieced this bit of information together from a German website, but here's a script that you can save as a file in your Pingus directory.

Open a text editor, paste this information in and save it to your computer.  You will need to change the PINGUS_DIR at the top of the file to go to your Pingus levels folder, but the default is probably where it is. Then edit your applications>games menu to have a new item, and make the launcher command be "sh /*path to this file*".

Then when you launch this file from your Games menu, you will be given a directory listing of all the additional levels in your computer.  Click on one to play it, or click "cancel" to start up Pingus normally.

Have fun!   :)



#!/bin/sh

PINGUS_DIR=/usr/share/games/pingus/data/levels/playable

cd $PINGUS_DIR
exec >/dev/null 2>&1
f=1
while [ "$f" != "" ]
do
  f="$(zenity --title="Last Level: $(cat ~/.pingus.last)" --file-selection)"
  [ "$f" != "" ] && echo $(basename $f) > ~/.pingus.last
  cd $PINGUS_DIR
  if grep -q "<pingus-demo>" $f /dev/null
  then
    pingus
  else
    pingus $f
  fi
  cd $(dirname $f)
done

---

### Post by happyhamster on 2008-02-11
Oooh, you just made my day! Script works great (after deleting the space in "pla yable").

BTW: some of those custom levels are *really* tough!

---

### Post by xen-uno on 2008-08-10
Works nice ... you can also set Pingus's start up rez by adding **-g *<hor-rez>*x*<vert-rez>*** to kmull's script as shown here ...

.
.
if grep -q "<pingus-demo>" $f /dev/null
then
pingus **-g 1900x1140**
else
pingus $f **-g 1900x1140 **
fi
.
.

... and yes, many of the levels that the script "unhides" are very rough and disfunctional ... and the ones that do work well are too damn hard!!! :)

---

### Post by Loirenzo_G on 2009-11-21
[SIZE=2]Gracious Greetings 2 EVERYBODY...

I Just to Be A Lemmings Fan, but I fell In Love Once Again with This New Version of it...

About this AWESOME PINGUS Game I Can Tell You a few simple things. :p

* If you follow this LINK [http://xzcallaway.synthasite.com/mariolemming.php](http://xzcallaway.synthasite.com/mariolemming.php)

and / or Download this File from the same Location

[http://xzcallaway.synthasite.com/resources/pinguslevels_1.0-1_i386.deb](http://xzcallaway.synthasite.com/resources/pinguslevels_1.0-1_i386.deb)

You'lll Be Able to Play those Hidden Levels, cause it will install a Special File in the GAMES section called "Pingus Levels". :KS

That's It, PROBLEM SOLVED !!! :popcorn:

Blessings All The Way from PANAMA !!![/SIZE]

---

