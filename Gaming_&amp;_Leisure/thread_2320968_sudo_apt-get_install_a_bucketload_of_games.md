---
title: "sudo apt-get install a bucketload of games"
date: 2016-04-19
forum: Gaming &amp; Leisure
---

### Post by West Swan on 2016-04-19
Good evening from Western Australia.

This is a bit weird perhaps.

I love Lubuntu which I put on older computers to donate to Pensioners, Students etc.   Well donate is perhaps slightly wrong.  I charge them $20 or a home cooked meal :)

What I want to do is create a Lubuntu Games Edition by doing some kind of **sudo apt-get install lots of games** type command.

That would be similar to my usual **sudo apt-get install libreoffice rgbpaint vlc aisleriot lubuntu-restricted-extras**  for regular programs.

Most of the computers are Pentium 4 with 1Gb Ram.

Silly question but has anyone actually created a list  like this?  It would save me a lot of time than manually choosing all the games and creating it from scratch.

I've tried SparkyLinux GameOver edition but can never update it properly.

Regards,

Paul

---

### Post by oldrocker99 on 2016-04-19
No list that I know of exists; you can find different genres in Synaptic by searching for "strategy," "first-person shooter," "role playing," etc.

There are also a lot of free-to-play Steam games, which require only a Steam membership.

PlayOnLinux will install a raft of commercial Windows games, including games from GOG.com, which are usually pretty low-priced.

---

### Post by deadflowr on 2016-04-20
For what it's worth,
you can simply create a text file listing all the games you want to install and run:
```
sudo apt-get install $(cat name-of-text-file-here)
```

Since the system is of the lower end, you'll have to try out various games yourself to see how well they play.
If they play nice, add the game to the list.
When you've compiled a nice list of decent games that'll play on those lower end systems, simply copy the text file to those systems to use for easy installation.

Not that that is what you are really after, but it's nice to have a standardized way of installing things you know will work, at least.
As opposed to simply having some meta-package that installs a bunch of stuff that cannot run half the time.
(and that list of stuff unusable will grow for machines of that ilk as time goes on)

Me two cents, anyway.

---

### Post by v3.xx on 2016-04-20
A game meta-pack.  I like the idea, but someone needs to build it.

What about using synaptic package manager?  A search gave me 661 hits and fairly easy to load from there.

[ATTACH=CONFIG]268465[/ATTACH]

---

### Post by deadflowr on 2016-04-20
Well kde has had meta-package of game for years: [kdegames]("http://packages.ubuntu.com/trusty/kdegames")
But then again, it's kde which will always mean adding a bunch of kde dependencies. 
They're mostly, fairly, lightweight games, though.
Another for what it's worth...

---

### Post by v3.xx on 2016-04-20
A meta-pack of lightweight games.  That sounds like a worthy venture.  Maybe even turn it into a PPA.

I would be willing to assist in such a project.

Anyone else game :P

---

### Post by mastablasta on 2016-04-20
install (use playdeb to get more), test, make sure they work and that they work well then re-master it into your own Linux Respin: [http://www.remastersys.org/](http://www.remastersys.org/)

---

### Post by West Swan on 2016-04-20
Hi Everyone,

Thanks very much for all your advice.

I had a thought.  SparkyLinux GameOver Edition is Debian based and uses LXDE if I am not mistaken.  Its minimum specs are lower than the computers I restore.

I want to make this as easy as possible for myself so I thought why not just get a list of the games on it and install them on Lubuntu.

It can't hurt to try right?  All the dependencies should sort themselves out etc.

Anyhow I am going to have a 'play' over the next few days and will get back to you good folk.

Regards,

Paul

---

### Post by West Swan on 2016-04-20
Hello,

Ok with acknowledgment that these games are installed on SparkyLinux GameOver Edition (I just prefer Lubuntu is all) and  a few hours later and I have done the following:


  sudo apt-get update
   
   
  Restart Computer
   
   
  sudo apt-get install 0ad 3dchess airstrike alienblaster amphetamine armagetronad asciijump asylum atomix balder2d barrage wesnoth berusky billard-gl biniax2 blackbox blobandconquer bloboats blobby blockout2 brainparty btanks bygfoot chromium-bsu desmume dosbox einstein extremetuxracer five-or-more flare foobillard four-in-a-row freedroid frozen-bubble funnyboat gcompris gnome-hearts gnome-klotski gnome-mastermind gnome-mines gnome-nibbles gnome-tetravex gnubik gnugo gtkatlantic gunroar holdingnuts iagno lbreakout2 lightsoff liquidwar ltris maelstrom gnome-mahjongg megaglest minetest mokomaze monsterz moon-lander nestopia netpanzer neverputt neverball openarena performous pingus playonlinux quadrapassel radiotray scorched3d slimevolley snake4 snowballz steam stella gnome-sudoku supertux super swell-foop tali tennix tetzle teeworlds tomatoes transcend warzone2100 widelands xmoto yabause zaz zsnes
   
   
  Restart Computer
   
   
  sudo apt-get autoremove
   
   
  sudo apt-get autoclean
   
   
  Restart Computer


I am unsure if the restarting of the computer is necessary?  But I did it anyhow.  I have 'quickly' tested all the games and can confirm that at least they all start  :-)    I haven't played any as such.


If there are any other games anyone thinks could be on a Lubuntu Games Edition then please feel free to let me know.  They would have to run on Pentium 4 era machines with 1Gb or less of Ram and an integrated graphics card.

Doing this has been so much fun :P

---

### Post by v3.xx on 2016-04-21
A bit late, but I did find three meta-packs.

[http://packages.ubuntu.com/xenial/games-adventure](http://packages.ubuntu.com/xenial/games-adventure)

[http://packages.ubuntu.com/xenial/games-arcade](http://packages.ubuntu.com/xenial/games-arcade)

[http://packages.ubuntu.com/xenial/games-board](http://packages.ubuntu.com/xenial/games-board)

---

### Post by West Swan on 2016-04-21
Hi v3.xx,

I know I can install via sudo apt-get install games-arcade etc   but   do you know if these are suitable for low spec machines or would I need to go through each individual game and see if it plays satisfactorily?

Thanks very much for the input :-)

Paul

---

### Post by mastablasta on 2016-04-21
> **West Swan said:**
> 

If there are any other games anyone thinks could be on a Lubuntu Games Edition then please feel free to let me know.  They would have to run on Pentium 4 era machines with 1Gb or less of Ram and an integrated graphics card.



there are a number of old DOS games that were released by authors. I am not sure if distribution is allowed but for dos games there is a way around (e.g. providing script to automate download and "install" on first run). among notable ones are TES: Arena and TES2: Daggerfall, C&C was also released as free ware, not sure about Red Alert. I am sure there are more such games. 

then you have remakes such as oolite and privateer.

I don't know what could/would happen if you added abandoned games. abandoned games are those that are still under copyright, but for various reasons no one can or will claim it (e.g. company that made the game went broke and no one took over from them). there is a whole bunch of them out there.

---

### Post by oldrocker99 on 2016-04-21
Abandonware is mostly still under copyright, and several old 90s games have been rereleased on Steam: The 7th Guest, Across the Rhine, Another World, Challenge of the Five Realms, The Chaos Engine, CommandHQ, DragonSphere, the Tex Murphy games, Wizardry 6 and 7, etc, etc.

ANY of those i mentioned will run fine & dandy on practically every old computer.

---

### Post by MikeCyber on 2016-04-24
I love mame for donkey kong, burgertime, pacman etc.

---

### Post by samue2 on 2016-04-28
This helped me alot to create a few packages for easy installation to another pc! such as software, gimp, and coding.

---

### Post by West Swan on 2016-04-28
I deleted this post as I asked a stupid question I could have googled myself in less than 30 seconds.

---

### Post by West Swan on 2016-04-28
Hi Sameue2,

As the original poster I am very happy we could all help.

I am still learning with Linux but I agree that being able to install multiple programs quickly is of great importance for those of us who want to install on multiple computers.

Cheers,

Paul

---

### Post by West Swan on 2016-04-28
Duplicate

---

### Post by West Swan on 2016-04-29
Hello again,

Another good one is  sudo apt-get install games-finest-light

This installs heaps of awesome light games just perfect for Lubuntu.

---

