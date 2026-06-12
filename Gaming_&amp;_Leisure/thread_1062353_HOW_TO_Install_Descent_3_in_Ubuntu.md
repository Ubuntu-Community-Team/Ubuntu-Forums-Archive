---
title: "HOW TO: Install Descent 3 in Ubuntu"
date: 2009-02-06
forum: Gaming &amp; Leisure
---

### Post by bobmatino17 on 2009-02-06
well i had a bit of trouble while installing D3 and thought i might a well help everyone else by telling them how...

first become root by:```
sudo bash
```

next cd to /media/cdrom0 (It is now usually called /media/Descent 3 - Disk 1, the command to get there would be...

```
cd '/media/Descent 3 - Disk 1'
```

next you should run setup.sh 

```
bash setup.sh
```

after you install D3, you may try to run it and get and error so...
(while in root)
```
ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
```
 it should run fine after that.

for any errors contact me.

_____

this also works in fedora, i tried it since i had the same problems. might work other distros, haven't tried it.

---

### Post by EdThaSlayer on 2009-02-07
Would be nice to state what this game is.

Taken from Wikipedia:
> "Descent 3 is the third game in the line of Descent computer games, well known for the use of six degrees of freedom and true 3D rendering technology."
and the story as Wikipedia states-
> "Previously in Descent II, Material Defender 1032 had narrowly escaped the destruction of an alien planetoid he was investigating on orders of the Post Terran Mining Corporation (PTMC), a megacorporation. He was about to return to Earth to collect his reward, but without warning, a malfunction occurred with the prototype warp drive in the ship he was flying."

Sounds pretty interesting.
From 1999 though.

---

### Post by bobmatino17 on 2009-02-07
i know the game is old... but for its age it has amazing graphics. It was slow in its time because of its requirements rarely being met back then. Even D1 and D2 have great graphics for how old they are. great games, all of them.

---

### Post by |-|ans on 2009-04-04
Wonderful to hear the possibility to install (using Jaunty Jackalope even). Can't wait to try the installation myself after the files are downloaded (very slow @ 1.5KB/s) *but* since Loki is closed -and- the website they refer to in my country does not have anything close have not much choice left... but, haven't played it for a long time anyway so patiently waiting to give it a try ;)

---

### Post by Naiki Muliaina on 2009-04-05
> **EdThaSlayer said:**
> 
From 1999 though.

Cooo is it that old? Think i just felt myself age a few years... I remember pre ordering the windows version and it feels like a couple of years ago ^^

---

### Post by bobmatino17 on 2009-04-05
i had some trouble with jaunty, although i can run quake 3 on jaunty, which i couldnt have on hardy...

---

### Post by |-|ans on 2009-04-05
Well, I can confirm your brief instructions worked great here! After installation copied the movie files from cd2 to the movies folder on the hdd and no disc required now as well. Only thing that is not right is the movie play... they corrupt the desktop (lowering the resolution dramatically) and the movie is almost transparant played on top of it. But, escape starts the game and it runs fine on 1280x960. At the time they had never heard of 1680x1050 widescreen I assume ;) WTG!

---

### Post by bobmatino17 on 2009-04-06
this may sound stupid, but i cant get D3 working... :(. It cant find version key. i cd'd to /usr/local/games to try to run it since thats how i ran quake3, but it didnt work. I recently went to jaunty, so its a tad different. if any other jaunty users have D3 please help!

---

### Post by bobmatino17 on 2009-04-25
Good News! I fixed the problem i had! If you get an Error that says something like "Can not find Descent 3 Version Key" try...

```
sudo chown *username* ~/.loki*
```

that should work.

if you want you can email me your videos (.dem files) of you playing D3 and i can help or just watch at

[COLOR="Red"]bobmatino@gmail.com[/COLOR]

to record a demo file, during game play hit "F5". A dialouge box should appear asking you what to name the file. You enter the name for it in, and you record. To finish the recording hit "F5" again.

---

### Post by Brebs on 2009-04-26
> **bobmatino17 said:**
> sudo chown ...
You must have been (well, most probably were) doing some weird messing around as root, in your home area, to get into that situation in the first place.

Files created by you in your home area are automatically read-writable by you, unless you've done something very weird yourself ;)

---

