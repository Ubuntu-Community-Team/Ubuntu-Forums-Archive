---
title: "Neverwinter Nights error"
date: 2005-11-20
forum: Gaming &amp; Leisure
---

### Post by Rumor on 2005-11-20
I'm relatively new to linux. I very much enjoy the game Neverwinter Nights. Today i installed it following the instructions from Bioware's site:

[http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

When I started the game, the screen went blank for a couple seconds then I was back to the desktop with this message in the terminal:

Fatal signal: Segmentation Fault (SDL Parachute Deployed)
./nwn: line 12: 25781 Segmentation fault      ./nwmain $@

My system ran NWN fine in windows:
Athlon xp3000+ processor 
nvidia 6800gt video card
768 Megs RAM

Any ideas?

---

### Post by Perfect Storm on 2005-11-21
And I guess that you have installed all the SDL libs?

---

### Post by Rumor on 2005-11-21
[QUOTE=Artificial Intelligence]And I guess that you have installed all the SDL libs?[/QUOTE]

Probably not, I'm still a newb. Which ones do I need to install?

---

### Post by Perfect Storm on 2005-11-21
Try with:

```

sudo apt-get install libsdl-gfx1.2 libsdl-image1.2 libsdl-mixer1.2 libsdl-net1.2 libsdl-sound1.2 libsdl-tff2.0-0

```
Then there should be a chance to get it to work.

---

### Post by Rumor on 2005-11-22
[QUOTE=Artificial Intelligence]Try with:

```

sudo apt-get install libsdl-gfx1.2 libsdl-image1.2 libsdl-mixer1.2 libsdl-net1.2 libsdl-sound1.2 libsdl-tff2.0-0

```
Then there should be a chance to get it to work.[/QUOTE]

Thanks for the reply. I get the following when I try to run the statement:

[COLOR="Blue"]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libsdl-tff2.0-0[/COLOR]

Is there something I have to put in my sources.list file to access that library?

---

### Post by Perfect Storm on 2005-11-22
Here's a copy of mine:
> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Non-free
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


Perhaps I wrote that one wrong, try check synaptic and look it up.

---

### Post by Rumor on 2005-11-23
[QUOTE=Artificial Intelligence]Perhaps I wrote that one wrong, try check synaptic and look it up.[/QUOTE]

I guess it's possible. I've checked [http://www.libsdl.org/index.php](http://www.libsdl.org/index.php) and can't seem to find the "missing" library. NWN still does not run. I'll have to dig a bit on the error message and see if I can find a solution. Thanks for your effort!
:smile:

---

### Post by bb002 on 2005-11-24
it should be ```
sudo apt-get install libsdl-gfx1.2 libsdl-image1.2 libsdl-mixer1.2 libsdl-net1.2 libsdl-sound1.2 libsdl-ttf2.0-0

```
on "libsdl-ttf2.0-0" you had "libsdl-tff2.0-0"  (the second 't' was a 'f'). Took me a whole 5 minutes of scratching my head to notice the difference.....

---

### Post by bb002 on 2005-11-24
I'm also having difficulty with NWN. I've installed the game using an installer script. Which basically extracted the archives of the 4 cd and applied the latest patch, I was to lazy to do it myself. Now when I run the nwn script. I am greeted with the cd-key prompt as expected but after 3-6 seconds the screen gets garbled up and locks up. i can alt+ctrl+f1 (have to hit f1 alot to make it register) to get to the console and kill off nwmain, then i can alt+ctrl+f7 back to  the desktop. I have to log out and back in otherwise I i have a 800X600 box clipping my desktop.

My system is almost identical to Rumor.
I have a 
AMD Athlon XP 3000+
Nvidia 6800
1GB RAM

The game ran fine in windows.

---

### Post by cdsboy on 2005-11-24
to both of you i would suggest getting the loki installer which installed and ran fine on my laptop. when playing it cannot load the modules but tha tis fixed by getting the patch of the loki site. when i play i have a weird silver flicker on the moddels but i fear that is just my video card acting up.

---

### Post by Rumor on 2005-11-24
[QUOTE=cdsboy]to both of you i would suggest getting the loki installer which installed and ran fine on my laptop. when playing it cannot load the modules but tha tis fixed by getting the patch of the loki site. when i play i have a weird silver flicker on the moddels but i fear that is just my video card acting up.[/QUOTE]

I'll give the installer you mention a try. Do you have a URL?

---

### Post by tim15856 on 2005-11-25
[QUOTE=Rumor]I'll give the installer you mention a try. Do you have a URL?[/QUOTE]
[http://www.linux-gamers.net/modules/news/article.php?storyid=528](http://www.linux-gamers.net/modules/news/article.php?storyid=528)

[http://www.lokigames.com/development/setup.php3](http://www.lokigames.com/development/setup.php3)

---

### Post by cdsboy on 2005-11-25
[http://liflg.org/?catid=6&gameid=65]("http://liflg.org/?catid=6&gameid=65") that is the exact place i downloaded it from

---

