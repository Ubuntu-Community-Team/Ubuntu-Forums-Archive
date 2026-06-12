---
title: "Minetest"
date: 2012-07-17
forum: Gaming &amp; Leisure
---

### Post by Sarys on 2012-07-17
Hey I have this free Minecraft clone called [Minetest]("http://minetest.net/"). It's good clone but there's no sound yet (I think there's no mobs ether). But I've heard there's mod that brings mobs is that right? So if someone could tell me some useful mods for that I'd be happy.

---

### Post by regor210 on 2012-07-19
I think your looking for Minetest 0.4
[http://minetest.net/0.4.php](http://minetest.net/0.4.php)
[http://minetest.net/forum/viewforum.php?id=11](http://minetest.net/forum/viewforum.php?id=11)

I hadn't tried Minetest for a while and I'm surprised at how far its come. I use github's wget Debian/Ubuntu instructions to compile Minetest 0.4.  I only payed for 10 minutes but I have to say wow its turning into a grate open source Minecraft clone. I'll have the kids try it tomorrow and see what they make of it.

---

### Post by Sarys on 2012-07-19
> **regor210 said:**
> I think your looking for Minetest 0.4
[http://minetest.net/0.4.php](http://minetest.net/0.4.php)
[http://minetest.net/forum/viewforum.php?id=11](http://minetest.net/forum/viewforum.php?id=11)

I hadn't tried Minetest for a while and I'm surprised at how far its come. I use github's wget Debian/Ubuntu instructions to compile Minetest 0.4.  I only payed for 10 minutes but I have to say wow its turning into a grate open source Minecraft clone. I'll have the kids try it tomorrow and see what they make of it.

But 0.4 is not out yet, right?

---

### Post by regor210 on 2012-07-19
No version of Minetest is what I would call stable 3.0 or 4.0.
If you use GNU/Linux/Ubuntu you will have to compile Minetest 4.0 from source, not too hard using the Debian/Ubuntu instructions. 

[https://github.com/celeron55/minetest/](https://github.com/celeron55/minetest/)

scroll down to
Compiling on GNU/Linux:

Three things you need to know to compile the game.

To open a terminal press ctrl+alt+t all at the same time.  Then cut and paste the commands you want to run into the terminal window one line at a time minus the $.
------------------------------------------------------------- 
In Ubuntu we use $ sudo apt-get....... 
you will only need to use sudo on the first line under Install dependencies.
--------------------------------------------------------------
type 
$ ls 
Before running the line below to see what number you got. Mine was celeron55-minetest-02fb912 so I ran $ cd celeron55-minetest-02fb912

$ cd celeron55-minetest-286edd4 (or similar)
--------------------------------------------------------------
The rest is easy.

---

### Post by Sarys on 2012-07-25
> **regor210 said:**
> No version of Minetest is what I would call stable 3.0 or 4.0.
If you use GNU/Linux/Ubuntu you will have to compile Minetest 4.0 from source, not too hard using the Debian/Ubuntu instructions. 

[https://github.com/celeron55/minetest/](https://github.com/celeron55/minetest/)

scroll down to
Compiling on GNU/Linux:

Three things you need to know to compile the game.

To open a terminal press ctrl+alt+t all at the same time.  Then cut and paste the commands you want to run into the terminal window one line at a time minus the $.
------------------------------------------------------------- 
In Ubuntu we use $ sudo apt-get....... 
you will only need to use sudo on the first line under Install dependencies.
--------------------------------------------------------------
type 
$ ls 
Before running the line below to see what number you got. Mine was celeron55-minetest-02fb912 so I ran $ cd celeron55-minetest-02fb912

$ cd celeron55-minetest-286edd4 (or similar)
--------------------------------------------------------------
The rest is easy.


I have no idea what to do....

---

### Post by madjr on 2012-07-26
since am subbed to some ubuntu blogs I just saw this earlier about minetest:

[http://www.iloveubuntu.net/free-open-source-minecraft-inspired-game-minetest-041-released-official-ppa-available](http://www.iloveubuntu.net/free-open-source-minecraft-inspired-game-minetest-041-released-official-ppa-available)

---

### Post by Sarys on 2012-07-26
> **madjr said:**
> since am subbed to some ubuntu blogs I just saw this earlier about minetest:

[http://www.iloveubuntu.net/free-open-source-minecraft-inspired-game-minetest-041-released-official-ppa-available](http://www.iloveubuntu.net/free-open-source-minecraft-inspired-game-minetest-041-released-official-ppa-available)

Thanks :)

---

### Post by cprofitt on 2013-03-11
The latest update -- that I loaded from PPA has sound now... I am starting to add mods to my server... if anyone has any interest I could do a tutorial for adding the mods.

---

### Post by superdaveozzborn on 2013-03-29
Mintest 0.4.5 was released some time ago, for any one that has had trouble compiling it I found this on the minetest forum and found it to be quite nice when upgrading to the latest development version.

For Ubuntu Users:
copy and past this intire one liner into the terminal, enter the sudo password, it will install the needed packages download the source, compile it, and start the game all in one shot.

> 
sudo apt-get install git-core build-essential libirrlicht-dev libgettextpo0 libfreetype6-dev cmake libbz2-dev libpng12-dev libjpeg8-dev libxxf86vm-dev libgl1-mesa-dev libsqlite3-dev libogg-dev libvorbis-dev libopenal-dev; git clone git://github.com/minetest/minetest.git;cd minetest/games; git clone git://github.com/minetest/minetest_game.git; git clone git://github.com/minetest/common.git; cd ..; cmake . -DENABLE_GETTEXT=1 -DENABLE_FREETYPE=1; cd src; make -j2; cd ../bin; ./minetest; echo -e "\n\nYou can run Minetest again by double-clicking \"minetest\" in the \"bin\" folder of the \"minetest\" folder in your home folder.\nYou can install mods in ~/.minetest/mods/minetest, too."

then when you want to play just use this command to start it again.
```
minetest/bin/./minetest
```

if you want to run a server
```
minetest/bin/./mintestserver --worldname NAMEOFWORLDHERE
```

I have also created a bitcoin mod for the game, no not real bitcoins but a bitcoin like theme to the game. :D now you are actually mining for bitcoins in the game, again not real Bitcoins, but a bitcoin theme / novelty item
if you would like to see some snap shots then check this out [http://www.distrogeeks.com/?p=7734](http://www.distrogeeks.com/?p=7734)

---

