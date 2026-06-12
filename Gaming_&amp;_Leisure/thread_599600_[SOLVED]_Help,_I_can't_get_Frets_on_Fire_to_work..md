---
title: "[SOLVED] Help, I can't get Frets on Fire to work."
date: 2007-11-01
forum: Gaming &amp; Leisure
---

### Post by neekz on 2007-11-01
Hi, I am a long time lurker for advice but I searched and searched but couldn't find anything about a certain error I get when I try to open Frets on Fire. I installed it via Synaptic package manager with the necessary files it asked for but when I try to open it I get this.

```
angel@angel-desktop:~$ fretsonfire
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 166, in __init__
    self.svg = SvgContext(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 78, in __init__
    self.setGeometry(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 91, in setGeometry
    geometry[2], geometry[3])
  File "/usr/share/games/fretsonfire/game/DummyAmanith.py", line 42, in SetViewport
    glViewport(x, y, w, h)
ctypes.ArgumentError: argument 3: <type 'exceptions.TypeError'>: wrong type
angel@angel-desktop:~$ 
```

 The screen goes black and tries to load up but just returns to the desktop with this in the terminal.
  I tried re installing it again through synaptic manager but still the same thing. My computer AMD 64, 1gb Ram, Nvidia 6800gt, Is it because the game is 32-bit?? Is there a work around???
 I am a linux noob any help would be greatly appreciated.

---

### Post by hikaricore on 2007-11-01
If you're using a 64bit kernel, and the application is 32bit, you can and will have problems.
Aside from that it may just be an issue with missing python packages.

I'm not familiar with the issue you mentioned though, just throwing out suggestions.

---

### Post by Hairy_Palms on 2007-11-01
the rep version is unusable for me, theyve screwed with the fonts and made it run ridiculously slow, try downloading the tarball from the [http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)

---

### Post by cogadh on 2007-11-01
Also just spitballing here, but it might help to install the ia32libs package, if you haven't already.

---

### Post by neekz on 2007-11-01
> **Hairy_Palms said:**
> the rep version is unusable for me, theyve screwed with the fonts and made it run ridiculously slow, try downloading the tarball from the [http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)

 Are you on X86 architecture??

> **cogadh said:**
> Also just spitballing here, but it might help to install the ia32libs package, if you haven't already.

  I just used synaptic, I haven't done anything else and wouldn't know where to begin to install ia32libs package.

---

### Post by cogadh on 2007-11-01
Either with Synaptic or from the terminal:
```
sudo apt-get install ia32libs
```

---

### Post by neekz on 2007-11-01
> **cogadh said:**
> Either with Synaptic or from the terminal:
```
sudo apt-get install ia32libs
```

```
angel@angel-desktop:~$ sudo apt-get install ia32libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32libs
```

 I have synaptic with universe and multiverse repositories but it didn't come up :(

---

### Post by cogadh on 2007-11-01
Sorry, the package name should be ia32-libs (forgot the dash).

---

### Post by discmaster on 2007-11-01
HI! 

If I may jump in here w/ a noob question; I have downloaded this from the FOF website, placed the file in my Home folder & extracted it. Now what? How do I install? I see no readme/install file to follow?

Thank you! :)

---

### Post by cogadh on 2007-11-01
[http://gaming.gwos.org/doku.php/guides:fretsonfire](http://gaming.gwos.org/doku.php/guides:fretsonfire)

That should help.

---

### Post by discmaster on 2007-11-01
Well, I was doing great until I got to this part; > Add the following;

#!/bin/bash

cd ~/.Games/FretsOnFire
sh FretsOnFire

Save (ctrl)+(o) and Save (ctrl)+(x)

Code:From there forward I am totally lost, which is not surprising for my level of experience...

---

### Post by cogadh on 2007-11-01
I don't really understand what you are lost on, but when you run the previous command in the terminal (the "nano ~/.Games/Frets..." one), that should have started the terminal based text editor Nano. All you need to do is add the text (from the "#!/bin/bash" to the "sh FretsOnFire") to the file, then press CTRL+O to save the file and CTRL+X to exit the editor. 

The next command is also to be entered in the terminal and it makes the game script executable, then launches the menu editor so that you can create a menu entry for the game.

If you have any other problems, be a little more specific about what exactly you don't understand, maybe I can be a little more specific with my suggestions.

---

### Post by neekz on 2007-11-01
> **cogadh said:**
> [http://gaming.gwos.org/doku.php/guides:fretsonfire](http://gaming.gwos.org/doku.php/guides:fretsonfire)

That should help.


 Excellent!! I followed that write up and now it loads up!! :guitar:

 Thanks for your help

---

### Post by Thelasko on 2007-12-09
> **neekz said:**
> Excellent!! I followed that write up and now it loads up!! :guitar:

 Thanks for your help

I am having the same problem you had.  Unfortunately the link posted no longer works.  What did you do to fix it?

---

### Post by Thelasko on 2007-12-09
Thanks to the[ Google cache]("http://64.233.167.104/search?q=cache:1-4e1mUT2tMJ:gaming.gwos.org/doku.php/guides:fretsonfire+ubuntu+gamers+arena+frets+on+fire&hl=en&client=firefox-a&gl=us&strip=1") I found the page.

It says:
> Before Installation

Make sure that the driver to your 3D graphic card is proper installed and working.
Check if your sourcelist is fully enabled (universe, multiverse and mediabuntu).

Next step is to download the right libs to make Frets On Fire work. To the terminal;

Code:

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install libsdl-mixer1.2 libsdl-ttf2.0-0

Done.
Installation

Download Frets On Fire Full linux version to your Desktop;

Download

To the terminal;

Code:

cd ~/Desktop
mkdir ~/.Games
tar zxfv FretsOnFire-1.2.451-linux.tar.gz -C ~/.Games

Done.
Launcher

Next thing is to make a launcher for Frets On Fire;

Code:

cd ~/Desktop
nano ~/.Games/FretsOnFire/Launch-FretsOnFire.sh

Add the following;

#!/bin/bash

cd ~/.Games/FretsOnFire
sh FretsOnFire

Save (ctrl)+(o) and Save (ctrl)+(x)

Code:

chmod +x ~/.Games/FretsOnFire/Launch-FretsOnFire.sh
alacarte

Go to Games and make a new entry;

Name: Frets On Fire
Command: sh /home/USERNAME/.Games/FretsOnFire/Launch-FretsOnFire.sh
Comment: Frets on Fire is a game of musical skill and fast fingers. The aim of the game is to play guitar with the keyboard as accurately as possible.

Icon: ~/.Games/FretsOnFire/data/icon.png

Enjoy! ^_^


---

### Post by disturbedite on 2007-12-09
> **Hairy_Palms said:**
> the rep version is unusable for me, theyve screwed with the fonts and made it run ridiculously slow, try downloading the tarball from the [http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)
just thought i'd note that this is a confirmed problem/[bug]("https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/154418"), not just speculation.

---

### Post by cogadh on 2007-12-09
> **Thelasko said:**
> I am having the same problem you had.  Unfortunately the link posted no longer works.  What did you do to fix it?
Just an FYI, the site is temporarily down, should be back soon. We wouldn't let the UGA just disappear without letting the community know about it somehow. :)

---

