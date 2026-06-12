---
title: "DEFCON strategy/war game now in repo"
date: 2007-07-17
forum: Gaming &amp; Leisure
---

### Post by skewer on 2007-07-17
Hi all

Just thought I should draw your attention to a post on the Introversion forums - someone has created Ubuntu packages for Defcon and put them in a shiny new repository. The game is basically a 6-player (max) online version of the Global Thermonuclear War scene from the end of the film *War Games*, playable at various speeds from real time to 20x real time (the world ends in about 15 minutes).

It takes just a couple of lines in a Terminal to get this game installed, or you can add the repository to your "software sources" of course. The packages are for a playable demo with (limited) online gaming, but the full version is only £10 or £15 ($20-30, EUR14-22) worldwide. 

Below are the required commands.

```
echo 'deb http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/ feisty main' | sudo tee -a /etc/apt/sources.list

sudo wget http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/introversion-packages-slimg-key.gpg -P /tmp

sudo apt-key add /tmp/introversion-packages-slimg-key.gpg

sudo aptitude update

sudo aptitude install defcon
```

Read more at [http://forums.introversion.co.uk/defcon/viewtopic.php?t=4981](http://forums.introversion.co.uk/defcon/viewtopic.php?t=4981) , and kudos to SlimG for making this possible.

(If you enjoy the game, please consider boosting the number of available non-demo servers by purchasing at [www.everyone-dies.com](www.everyone-dies.com))

---

### Post by slimg on 2007-07-18
I've just updated the defcon package so the vector icon should work on Gnome, it would be nice if someone could report if the defcon icon is viewable after install in Gnome.

Some Defcon Eyecandy/Screenshots:
[[img]http://www.everybody-dies.com/screenshots/t_screenshot4.jpg[/img]](http://www.everybody-dies.com/screenshots/screenshot4.jpg) [[img]http://www.everybody-dies.com/screenshots/t_screenshot3.jpg[/img]](http://www.everybody-dies.com/screenshots/screenshot3.jpg) [[img]http://www.everybody-dies.com/screenshots/t_defcon bigworld.jpg[/img]](http://www.everybody-dies.com/screenshots/defcon bigworld.jpg) [[img]http://www.everybody-dies.com/screenshots/t_screenshot2.jpg[/img]](http://www.everybody-dies.com/screenshots/screenshot2.jpg) [[img]http://www.everybody-dies.com/screenshots/t_pcgamer1.jpg[/img]](http://www.everybody-dies.com/screenshots/pcgamer1.jpg) [[img]http://www.everybody-dies.com/screenshots/t_screenshot1.jpg[/img]](http://www.everybody-dies.com/screenshots/screenshot1.jpg)

Ps. Thanks skewer for posting this :)

---

### Post by Cappy on 2007-07-18
```

$ sudo aptitude update
Get:1 http://download.introversion.co.uk feisty Release.gpg [481B]
Ign http://download.introversion.co.uk feisty/main Translation-en_US            
Get:2 http://download.introversion.co.uk feisty Release [1549B]
..... other junk .....
$ sudo aptitude install defcon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package matching "defcon".  However, the following
packages contain "defcon" in their description:
  cl-plus 

```

Must be because I'm running 64-bit. I'll use the loki installer.

---

### Post by slimg on 2007-07-18
> **Cappy said:**
> Must be because I'm running 64-bit. I'll use the loki installer.I should've made it more clear that Defcon is only compiled for x86 (32-bit) systems, sorry!
I've already asked if they could compile it to amd64 (64-bit), but they didn't have the capacity to alter the code for amd64 (64-bit) atm.

---

### Post by cmat on 2007-07-18
I never knew defcon was free. It was one of those game that killed tonnes of time on my laptop when I had free time.

---

### Post by skewer on 2007-07-18
It's not free, but the demo is very feature-rich. 

The full version lets you host games up to 6 players & customise all kinds of gameplay options, whilst the demo lets you host 2 player default-settings online wars.

However, demo users can still join 6-player games hosted by someone who has bought the game, but only 1 demo user can join each of these servers.

Overall there's a lot of fun to be had with 2 players, and the option to join bigger/custom games is a good taster of what the £10 would get you.

---

### Post by cmat on 2007-07-18
It's a good game. Makes you want to get a massive projector screen in your basement and a boardroom table.

---

### Post by zekopeko on 2007-07-18
> **slimg said:**
> I've just updated the defcon package so the vector icon should work on Gnome, it would be nice if someone could report if the defcon icon is viewable after install in Gnome.

Some Defcon Eyecandy/Screenshots:
[[img]http://www.everybody-dies.com/screenshots/t_screenshot4.jpg[/img]](http://www.everybody-dies.com/screenshots/screenshot4.jpg) [[img]http://www.everybody-dies.com/screenshots/t_screenshot3.jpg[/img]](http://www.everybody-dies.com/screenshots/screenshot3.jpg) [[img]http://www.everybody-dies.com/screenshots/t_defcon bigworld.jpg[/img]](http://www.everybody-dies.com/screenshots/defcon bigworld.jpg) [[img]http://www.everybody-dies.com/screenshots/t_screenshot2.jpg[/img]](http://www.everybody-dies.com/screenshots/screenshot2.jpg) [[img]http://www.everybody-dies.com/screenshots/t_pcgamer1.jpg[/img]](http://www.everybody-dies.com/screenshots/pcgamer1.jpg) [[img]http://www.everybody-dies.com/screenshots/t_screenshot1.jpg[/img]](http://www.everybody-dies.com/screenshots/screenshot1.jpg)

Ps. Thanks skewer for posting this :)

i just get a generic icon in the menus.

---

### Post by Cappy on 2007-07-18
The .run doesn't work for 64-bit it just gives errors. The defcon tar.gz works perfectly, I didn't even need to install or download any libraries since they came in the /libraries directory. I already have an extremely large amount of i386 libraries installed from getlibs so it may be that too.
I played the game for about an hour, I like it so far. I kind of wish there was a faster mode for waiting, I think I spent about 10 minutes just sitting here on the highest speed setting killing some random enemy cities.

---

### Post by Cappy on 2007-07-19
Okay .. well I take back my statement about the game being too slow. That was just the tutorial. 

I just played a few games against the AI for 3 hours and it was awesome. Sweet game and addicting! =P

---

### Post by kiv on 2007-07-19
I freaking love this game! I've played before the days of Ubuntu... time to buy it for Ubuntu me thinks!

---

### Post by skewer on 2007-07-21
If you already bought a license the code will work on any system - it can only be used in one place at a time, which is ideal for dual-boot setups (or people who don't play with themselves much)...

---

### Post by xhizors on 2007-08-01
I used to love this game. Funny you should say that. I just bought a cheap projector off ebay ;) i'm going to hook it up to my computer and project the side of my house lol. But seriously, defcon is amazing.

---

### Post by xhizors on 2007-08-01
Also, I wouldn't even refer to it as purchasing. More so donating to one of the few remaining garage developers.

---

### Post by xhizors on 2007-08-01
> **slimg said:**
> I've just updated the defcon package so the vector icon should work on Gnome, it would be nice if someone could report if the defcon icon is viewable after install in Gnome.



Nah dude. No icon..


Anyway. Any ideas for the error "Failed to set screen modeterminate called without an active exception
Aborted (core dumped)
" 

when trying to run??
that's through the terminal.
when i just run the app, nothing ever happens...

---

### Post by StooJ on 2007-09-18
Just installed on a (fairly) clean installation of Feisty and no icon in the menu.

I can live without the icon for a while, but it'd be nice to have one at some point in the future.

When I manually try to change the application menu icon, the icon browser doesn't seem to be able to see svgz files. Perhaps if it were replaced with a normal uncompressed svg it would work straight out of the box? I'm guessing, a linux beginner here.

Anyway, many thanks for making this awesome game available. Now I need to figure out how to install my full versions of [Uplink]("http://uplink.co.uk/") &  [Darwinia]("http://www.darwinia.co.uk/") as well.

---

