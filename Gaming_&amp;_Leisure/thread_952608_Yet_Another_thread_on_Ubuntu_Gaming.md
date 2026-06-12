---
title: "Yet Another thread on Ubuntu Gaming"
date: 2008-10-19
forum: Gaming &amp; Leisure
---

### Post by evilkastel on 2008-10-19
OK, I found myself a few days ago dual booting only to play s4 league and DotA in windoze. Then i decided...  i'll like to do my gaming in linux. I'm just too lazy to reboot just to play, and in the other hand I do not, (and won't for that matter) use cedega or wine, or virtualbox. If i wanted to run a windows game on linux by creating a virtual windows.... I'll reboot and do it on the real windows. For any matter, my XP is legal and i like ubuntu that much, I know is not the best GNU/linux, but works well for me. So, i've tested a few games, and they're not dissapointing, altough FPS is not so much my thing.  The reason I made this post is because I'll like all of you to tell me what is your favorite linux game, hopefully why, and thats all. Also, if anyone knows a Third person shooter FREE in linux, I'll make a shrine and venerate you. thats pretty much it. (this may be repost, but you find a lot of posts about OSS games vs Commercial games, and most of the "helpful" topics just link to linux games.org.. jeez... we have google you know... we'll like other users opinion.)

---

### Post by Perfect Storm on 2008-10-19
TPS?
[Blob Wars II: Blob & Conquer](http://gaming.gwos.org/doku.php/games:alphabetical:b:blob_wars_episode_ii) might be something.

---

### Post by evilkastel on 2008-10-19
yeah, I downloaded it but I'm on x64 and the deb won't install. I'm currently seeking for a way to make it run.

---

### Post by Perfect Storm on 2008-10-19
If like some adventure, you could download the source and try compile it.

---

### Post by Perfect Storm on 2008-10-19
Wrote it down for you how to compile it;
(note this is tested in 8.10)

First installing required libs, headers and -development packages
```
sudo ap-get update && sudo apt-get upgrade
sudo apt-get install build-essential 
sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev zlib1g-dev libgl1-mesa-dev libglu1-mesa-dev
```


Doenload the source to your Desktop, then 
This one, compile and install;
```
cd ~/Desktop
tar zxfv blobAndConquer-1.02-1.tar.gz
cd blobAndConquer-1.02
make 
sudo make install
cd
blobAndConquer
```

---

### Post by evilkastel on 2008-10-19
this is not what i had in mind, yet is really funny and, well i'm satisfied. thanx you very much, for that compiling job. I am a total noob and that way i learned a bit and got the satisfaction of playing something i compiled (well, you compiled). thanx!

---

### Post by wingnux on 2008-10-20
There's a REALLY GOOD shump game on linux with very good graphics and gameplay but I can't remember the name at the moment, I'll look it up when I come back from work ;)

You could always try searching happypenguin.org.

EDIT: Here are some nice entries I've found on getdeb.net (haven't found the one I was talking about, tough)

[http://www.getdeb.net/app/Alien+Blaster](http://www.getdeb.net/app/Alien+Blaster)

[http://www.getdeb.net/app/GridWars+2](http://www.getdeb.net/app/GridWars+2)

[http://www.getdeb.net/app/Open+Tyrian+Enhanced](http://www.getdeb.net/app/Open+Tyrian+Enhanced)

---

