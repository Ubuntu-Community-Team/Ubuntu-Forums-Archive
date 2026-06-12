---
title: "low graphics but fun games"
date: 2008-03-28
forum: Gaming &amp; Leisure
---

### Post by hiro nakamatty on 2008-03-28
can someone please help me, are there any multiplayer online games that do not require an exceptional graphics card, as mine is not too great.


thanks/ matty

---

### Post by Wobedraggled on 2008-03-28
Enemy territory is older and still has active players.

For even more basic graphics.

freeciv
Teeworld
 
I'm sure there are others, but that is a good start.

---

### Post by basketcase421 on 2008-03-28
It could help a little to know what your computer's specs are.  There are quite a few generations of "old" games, requiring different levels of hardware.

---

### Post by YotoshiWii on 2008-03-28
I'm very interested to see how this post will turn out. I also am on the lookout for "Low-End" MMORPG's. I'm on an IBM T40.

Intel Mobile Pentium M (Centrino) 1.3GHz
512MB DDR 266MHZ
32mb RADEON 7500


What can anyone recommend?

I was really looking forward to playing "The Mana World" But the game can't connect to the server. :(

---

### Post by Perfect Storm on 2008-03-28
> I was really looking forward to playing "The Mana World" But the game can't connect to the server. 

You properly need to install the latest version of Mana world.


See if [Dofus](http://gaming.gwos.org/doku.php/games:alphabetical:d:dofus) is something your computer can run. It's not GPL but freeware.

---

### Post by YotoshiWii on 2008-03-28
Yeah, i looked into Dofus, but i dont agree with paying a monthly subscription to play games. I'll happily go out and legally purchase a game, just not "pay to play".

Yeah, i'm almost sure it's the latest version of Mana World i have. It was freshly installed around a hour ago, downloaded from the repositories.

---

### Post by Perfect Storm on 2008-03-28
You can play dofus free. There's two diffrent account types. A free and pay2play.

Mana world in the repo is a version behind.

---

### Post by YotoshiWii on 2008-03-28
Oh, ok thanks. So is there a way i can update it? or is it best to just download the client from the website?

Dofus looks nice and sounds nice - I may check it out later. But i do prefer my "Low-End" games. :D

---

### Post by Perfect Storm on 2008-03-28
You have to download its source codes and compile it.

---

### Post by YotoshiWii on 2008-03-28
Yeah.... I dunno how to do that. lol. Kinda n00ibish with Ubuntu you see.

---

### Post by Perfect Storm on 2008-03-28
If you wait a bit, Hardy have the latest version of TMW.

---

### Post by Perfect Storm on 2008-03-28
ok I have done it for you. Uninstall your mana world.
NOTE: This have been tested on Ubuntu 7.10 64-bit Gnome


Dependencies:
```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install build-essential checkinstall
sudo aptitude install libsdl1.2-dev libsdl-image1.2-dev libsdl-net1.2-dev libsdl-mixer1.2-dev libguichan0-dev libphysfs-dev libexpat1-dev libcurl4-openssl-dev libgl1-mesa-dev libglu1-mesa-dev liballegro4.2-dev
```

Latest version og Guichan (needed):
```
cd ~/Desktop
wget http://guichan.googlecode.com/files/guichan-0.7.1.tar.gz
tar zxfv guichan-0.7.1.tar.gz
cd guichan-0.7.1
./configure --prefix=/usr
make
sudo make install

```

Mana world:
```
cd ~/Desktop
wget http://prdownloads.sourceforge.net/themanaworld/tmw-0.0.24.tar.gz?download
tar zxfv tmw-0.0.24.tar.gz
cd tmw-0.0.24
./configure
make
sudo checkinstall
```

---

### Post by YotoshiWii on 2008-03-28
Ok, thanks a lot dude!!! I'll give it a bash just now. :D

---

### Post by Perfect Storm on 2008-03-28
ok, I have written it into the 64-bit guide + how to install the music: [http://gaming.gwos.org/doku.php/guides:64bit:the_mana_world](http://gaming.gwos.org/doku.php/guides:64bit:the_mana_world)

---

### Post by YotoshiWii on 2008-03-28
Thanks for all that help dude, but when i get to the last step i get this - 

make: *** No rule to make target `install'. Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


Any ideas? :S

---

### Post by Perfect Storm on 2008-03-29
in which part?
Can you attach a text file with all the in/output? It makes it easier to see where the error is.

---

### Post by YotoshiWii on 2008-03-29
It's when i do "./configure" on the last part - i get this - 

checking for curl_global_init in -lcurl... yes
checking for xmlInitParser in -lxml2... no
**[SIZE="4"]configure: error:  *** Unable to find libxml2 library (xmlsoft.org)[/SIZE]**

any ideas? :confused:

---

### Post by Perfect Storm on 2008-03-29
```
sudo aptitude install libxml2-dev
```

The guide was corrected some hours ago.

---

### Post by YotoshiWii on 2008-03-29
Thanks a million for all your help dude - thats everything now working. Although i still encounter the same problem when i try to play - "Error - Couldn't Connect To Remote Host".

---

### Post by Perfect Storm on 2008-03-29
Are you behind some kind of proxy/firewall?

---

### Post by YotoshiWii on 2008-03-29
Nah dude, none. (that i know of).

---

### Post by Perfect Storm on 2008-03-29
Try and see if any other mmorpg games are doing the same (can't connect).


EDIT: Found this thread at Mana world forum: [http://forums.themanaworld.org/viewtopic.php?f=7&t=3833&hilit=can%27t+connect+server](http://forums.themanaworld.org/viewtopic.php?f=7&t=3833&hilit=can%27t+connect+server)

---

### Post by YotoshiWii on 2008-03-29
ok, downloading AlienArena - I'll see if it works and let you know

---

### Post by Perfect Storm on 2008-03-29
Did you see my edit of the post above?

---

### Post by Lord Illidan on 2008-03-29
Battle for Wesnoth is another nice game. It has multiplayer capability - it's a 2D turnbased strategy game.

---

### Post by YotoshiWii on 2008-03-29
Yeah i got the edit - But unfortunatly it still wont connect. AlienArena was taking to long, so i downloaded "PenguPop". I'm able to play that online perfectly fine.

I tried the other server in accordance to what was stated through the link there, but still having no luck. :confused:

I really appreciate all this - You've put a lot of time into getting this to work for me. :)

---

### Post by nofrendo on 2008-04-27
I would definitely reccommend downloading teeworlds. It is a really fun, fast paced 2d shooter... it's the kind of game your mom or girlfriend would play... not... cute... but kinda cartoony. And a lot of fun

add in software sources
[http://ppa.launchpad.net/jscinoz/ubuntu](http://ppa.launchpad.net/jscinoz/ubuntu) hardy main

and then do
sudo apt-get install teeworlds

---

