---
title: "How To Game....?"
date: 2008-06-03
forum: Gaming &amp; Leisure
---

### Post by RadarBat on 2008-06-03
[SIZE="4"]I know nothing about gaming - in Linux or Windows. I have had a lot of time on my hands, and I am building what, I believe, may be a gaming machine....OCZ GameXStream 700W PSU, ASUS M3A Mobo, AMD Phenom X4 2.4 GHz CPU, 4Gigs 800 MHz Corsair RAM, EVGA GeForce 9600 GT PCIE 2.0 video card, NZXT Apollo Case /w 3 120mm Fans (Will this cool sufficiently?). 
    I want to run open source games in Ubuntu 8.04. I really can't afford Windows & Windows games. Are there games available, and where can I find them? Is it a great deal of trouble to install and run them? 
    Any advice/links would be appreciated.     Ben - RadarBat[/SIZE]

---

### Post by abhiroopb on 2008-06-03
good places to start [http://www.linuxgames.com/](http://www.linuxgames.com/)
bit old: [http://techgage.com/article/top_10_free_linux_games/](http://techgage.com/article/top_10_free_linux_games/)

Most linux games can be run with a system about a quarter of the power you are building. If you want a TRUE gaming machine I recommend installing XP, and using various tweaks to make it run faster.

You can use wine (winehq.com) which basically allows you to install SOME windows software, however, this is highly buggy, especially with a lot of new games. 

Again if you want a truly powerful gaming machine use XP.

---

### Post by Perfect Storm on 2008-06-04
Open Source game list: [http://gaming.gwos.org/doku.php/games:gpl](http://gaming.gwos.org/doku.php/games:gpl)

---

### Post by mikeym on 2008-06-04
Just thought I'd mention that there is nothing wrong with linux as a gaming platform, but linux gaming has all but dried up with the increased popularity of the XBox. 

Developers appear to be under pressure to release games as DirectX only, no openGL; this makes linux releases impossible. Mac seems to be suffering for the same reason.

Please encourage everyone you know not to support the XBox and refuse to buy one.

---

### Post by RadarBat on 2008-06-04
_Ubuntu Gamers Arena_ in your signature links to a graphic and nothing more.
Thanks again.....................Ben................RadarBat

---

### Post by Perfect Storm on 2008-06-04
You may have trouble with your browser see if this is better;
[http://ubuntu-gamers-arena.org/](http://ubuntu-gamers-arena.org/)

or 

[http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php)

---

### Post by RadarBat on 2008-06-04
I now have my new system up and running Ubuntu 8.04 64-bit. I looked at the Nvidia site to find drivers for my EVGA GeForce 9600 GT card, and the instructions for installing the driver are major surgery. Is there a simpler way (or did Hardy set up the card when I installed the OS)??
I just want to play a game.............RadarBat

---

### Post by Grishka on 2008-06-04
> **RadarBat said:**
> I now have my new system up and running Ubuntu 8.04 64-bit. I looked at the Nvidia site to find drivers for my EVGA GeForce 9600 GT card, and the instructions for installing the driver are major surgery. Is there a simpler way (or did Hardy set up the card when I installed the OS)??
I just want to play a game.............RadarBat

try System/Administration/Hardware Drivers from the menu.

---

### Post by Perfect Storm on 2008-06-05
> **Grishka said:**
> try System/Administration/Hardware Drivers from the menu.

That card is not supported in the v169 driver that comes with Ubuntu.

[quote=RadarBat]I now have my new system up and running Ubuntu 8.04 64-bit. I looked at the Nvidia site to find drivers for my EVGA GeForce 9600 GT card, and the instructions for installing the driver are major surgery. Is there a simpler way (or did Hardy set up the card when I installed the OS)??
I just want to play a game.............RadarBat [/quote]

The EVGA is not list but you could give it a go.
```
[size=1]    * Quadro FX 3600M
    * GeForce 9800 GX2
    * GeForce 9800 GTX
    * GeForce 9600 GT
    * GeForce 9600 GSO
    * GeForce 9500M GS
    * GeForce 8400
    * GeForce 8400 GS
[/size]
```

Fiest you can try with Envy: Install **envyng-gtk** to install the driver. **envyng-gtk** is in synaptic Package Manager. See if version 173.14.05 is available there.


Manually;
Just remember that Linux is case sensitive
Download the driver to your Desktop
[Download](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html)

Open the terminal and type (copy/paste);
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential xserver-xorg-dev
sudo apt-get remove nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-kernel-common nvidia-settings
```

Next you need to press **<ctrl>+<alt>+<F1>** note it will take out of X (you'll now work in CLI), so you might copy the steps before going further.

```
sudo /etc/init.d/gdm stop
cd ~/Desktop
sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run
```

Note you'll be greet with some questions. Go with its own suggestion.

```
sudo nano /etc/X11/xorg.conf
```

Find where it says
```
[size=1]Section "Device"
	Identifier	"Configured Video Device"[/size]
```

and add;

**Driver "nvidia"**

Save [ctrl]+[o] and exit [ctrl]+[x]

then
```
sudo /etc/init.d/gdm start
```

---

### Post by Novega on 2008-06-05
Looks like manual install is the way to go. I also have a 9600GT and I had to re-install my video driver after the kernel update yesterday, envyng did _not_ have a suitable driver yesterday (maybe it's available today but it's doubtful)

I've been manually installing the beta driver every time a new kernel comes out, since my video settings get reset *(I've only been using linux since last month so I'm not sure if theres a workaround for this problem)* but the good news is that we no longer have to use _BETA_ drivers...the 9600GT is supported in the newest Nvidia released driver.

I'd recommend you print out the instructions Artificial Intelligence gave and follow them whenever you need to re-install the driver, you won't have any problems.

Good Luck :)

---

### Post by eragon100 on 2008-06-05
If you are just playing open-source games because they are free and not out of ideology, don't forget savage 1: [http://www.newerth.com]("http://www.newerth.com")

It's a great game, and it will have a decent speed on that monster you're building (200 fps or something, probably :lolflag:)

---

### Post by RadarBat on 2008-06-05
The copy of "envyng-gtk" that I installed was version 1.1.1ubuntu1  -Will this work?

NEVERMIND - The Nvidia driver is installed. Thank you again for your complete, detailed instructions. 

Update:  I have lost the minimize, maximize,and close buttons on my browser....I lost the top panel for a minute, but got it back. The screen jumps every time I do something on the browser....is this normal?    
.................Ben

Another update:  Everything is back to normal. (Wonder what I did?)

---

### Post by Perfect Storm on 2008-06-05
It sometime happen with compiz (still young, not bugless). Install fusion-icon (and also advance setting for compiz if you want to change/add cool effects and themes for compiz);

```
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra emerald fusion-icon
```

System tab ---> Preferences ---> Sesseions
or simple type:
```
gnome-session-properties
```

Press the "Add" button.

Name: Fusion Icon
Command: fusion-icon

Done. Now Fusion Icon starts up every time you starts up Ubuntu. Via Fusion Icon you can set Compiz and Emerald Decoration. If it fails you can quickly use it to reload.

When gaming you can disable Compiz (Compiz sometimes interfer when you gaming).

---

### Post by RadarBat on 2008-06-06
> Now Fusion Icon starts up every time you starts up Ubuntu. Via Fusion Icon you can set Compiz and Emerald Decoration. [COLOR="Red"]If it fails you can quickly use it to reload.[/COLOR]
What do you mean by "fails" and "reload"?

What are: MMORPG, RTS, and TBS ?

---

### Post by jualin on 2008-06-06
"fails" and "reload" means that sometimes Compiz doesnt load properly or you may want to reload it cause you lost the Minimize, Maximize and Close Buttons. To do this open Compiz Fusion Icons from the Applications Tab and look for the Compiz Fusion Icon running quietly on the notification bar. There you can right click on it to disable Compiz and enable Metacity (Gnome default Window Manager, no 3D) or to reload Compiz. Hope this clarifies a little bit.

---

### Post by Perfect Storm on 2008-06-07
> What are: MMORPG, RTS, and TBS ?

MMORPG = Massive Multiplayer Online Role Playing Game 
RTS = Realtime strategy
TPS = Third Person Shooter

---

### Post by ikki_72 on 2008-06-07
It's just seems weird for someone who could affords those stuff to be asking about how to play games...

But how's your journey so far?

---

### Post by ikki_72 on 2008-06-07
It's just seems weird for someone who could affords those stuff to be asking about how to play games...

But how's your journey so far?

---

### Post by RadarBat on 2008-06-07
I have had a lot of help from Artificial_Intelligence, but I am kinda stuck. I made a large debt to be able to build a gamer computer, and now I need free (open source) games to play. I used Dapper Drake for 6 months, but had problems with drivers (on non-gamer computers), and I decided to wait until a pretty much PNP OS came out. I have forgotten all I knew about Ubuntu in the last 2-3 years. Now I am just taking it one step at a time. Do you have any links to free Linux (Ubuntu) games?  Ben

---

### Post by RadarBat on 2008-06-07
> **Artificial Intelligence said:**
> You may have trouble with your browser see if this is better;
[http://ubuntu-gamers-arena.org/](http://ubuntu-gamers-arena.org/)

or 

[http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php)

I went to the 64-bit Gamers Arena and attempted to install Doomsday. I downloaded "deng-1.9.0-[COLOR="Blue"]beta5[/COLOR].tar.gz" and the install would go no further. I **was** in the Desktop folder. I noticed that your instructions had:

```
tar zxfv deng-1.9.0-[COLOR="Red"]beta5.1[/COLOR].tar.gz
cd deng-1.9.0[COLOR="Red"]-beta5.2[/COLOR]/deng-1.9.0-[COLOR="Red"]beta5.1[/COLOR]/doomsday/build

```

EDIT:  I changed the code "tar zxfv deng-1.9.0-[COLOR="Red"]beta5.1[/COLOR].tar.gz" to "tar zxfv deng-1.9.0-[COLOR="Blue"]beta5[/COLOR].tar.gz" and it unpacked the tarball, but would not do the next step.

EDIT:  I have "cd" to "deng-1.9.0-beta5", but I don't know how to "build" from here.

EDIT:  I just noticed on the doomsday website that the Doomsday 1.9.0-beta5.2 has been pulled.

EDIT:  I have gotten to this and cannot move the icon:

> ben@ben-desktop:~/Desktop$ sudo mv doomsdayicon.png /usr/local/share/gdoomsday
mv: cannot stat `doomsdayicon.png': No such file or directory
EDIT:  I downloaded the Link instead of the icon. I have finished installing Doomsday. Hurrah!!

Thanks for your work on the Gamers Arena. I shall contribute.  Ben....RadarBat

---

### Post by RadarBat on 2008-06-08
gDoomsday (Doom II) wants the path to the .WAD files. I can't find them. It's late here: I will hopefully have your answer tomorrow....Ben

---

### Post by Perfect Storm on 2008-06-08
I don't use that game, but so far as I know the original games are required.

---

### Post by meborc on 2008-06-08
i would go to [www.enemyterritory.com](www.enemyterritory.com) and try the linux demo... it is free, you can only play 1 map, but it is the best gaming experience i have had so far... turning all the graphics up, very nice extra eyecandy will appear inside the game :)

---

### Post by RadarBat on 2008-06-08
Thank you, but your link leads me to a blank page. Artificial_Intelligence said I may have something wrong with my browser. (Compiz?)

---

### Post by RadarBat on 2008-06-08
> **Artificial Intelligence said:**
> I don't use that game, but so far as I know the original games are required.
I cannot find a demo of Doom to get the .WAD files, so, for now, I am dropping Doomsday.

I am interested in Arkanoid: Space Balls. The install guide says to be sure my sourcelist is in order. How do I do that?

---

### Post by Grishka on 2008-06-08
> **RadarBat said:**
> I cannot find a demo of Doom to get the .WAD files, so, for now, I am dropping Doomsday.

I am interested in Arkanoid: Space Balls. The install guide says to be sure my sourcelist is in order. How do I do that?

try Freedoom: [http://freedoom.sourceforge.net/](http://freedoom.sourceforge.net/). it's a free alternative to commercial Doom. should play more or less the same.

as for Arkanoid: Space Balls, it seems that the installation instructions are for 64-bit system only, but don't worry about that. just download the game, unpack and run. most of the stuff in installation guides deals with making menu entries for the games, and stuff like that, but it's not strictly necessary.

---

### Post by RadarBat on 2008-06-08
I am running 8.04-64 on a 64-bit system. I now have "freedom-iwad-0.6.2" on my desktop. What do I do with it?

EDIT: I ran gDoomsday and entered Doom2.wad as the .wad file and tried to run Doomsday. It ran for a bit and then had a "Segmentation Fault".

---

### Post by Grishka on 2008-06-08
> **RadarBat said:**
> I am running 8.04-64 on a 64-bit system. I now have "freedom-iwad-0.6.2" on my desktop. What do I do with it?

it would be most convenient to use a frontend to manage your WADs. isn't there a Snowberry program bundled with Doomsday Engine? you can use that. or run doomsday with -file option, followed by the path to the WAD file.

edit: umm, sorry, I misunderstood you. seems you already have a frontend. don't know about your error, may be a bad Doomsday Engine version.

---

### Post by RadarBat on 2008-06-08
I do have a frontend (snowberry?). Sorry, I am stumbling in the dark. I'm a newbie. Iused Dapper Drake for 6 months, but have forgotten everything since then. Thanks for your help....Ben

---

### Post by Grishka on 2008-06-08
> **RadarBat said:**
> I do have a frontend (snowberry?). Sorry, I am stumbling in the dark. I'm a newbie. Iused Dapper Drake for 6 months, but have forgotten everything since then. Thanks for your help....Ben

gDoomsday is a frontend to Doomsday Engine. but I've never used this one myself. Snowberry is bundled with Doomsday Engine, you might try it. but if it won't work for you (Doomsday Engine has gotten a bit buggy some time ago), then perhaps you'll have more luck with one of these: [http://doom.wikia.com/wiki/Source_ports#Unix.2FUnix-like/](http://doom.wikia.com/wiki/Source_ports#Unix.2FUnix-like/). take your pick. one of these is bound to work.

---

### Post by ikki_72 on 2008-06-14
Another few great FPS i'd suggest:
Urban Terror [http://www.urbanterror.net](http://www.urbanterror.net)
OpenArena [http://openarena.ws/](http://openarena.ws/)
World of Padman [http://www.worldofpadman.com/](http://www.worldofpadman.com/)
True Combat: Elite [http://www.truecombat.us/](http://www.truecombat.us/)

Remember to read their documentations though. But OpenArena can be downloaded with **apt-get**, so is Alien Arena

---

### Post by doorknob60 on 2008-06-14
If you like games like Guitar Hero and rock band, definately look into Frets on Fire with the Alarian mod: [http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=20933](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=20933)

It's probably my favorite open source game ever made (for now at least lol). You'll need songs to go along with it: [http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=SF;f=5](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=SF;f=5)

You might need to sign up for the frets on fire forums first. Also, I can help you set it up (it's not the easiest thing in the world, but it's not too hard).

---

