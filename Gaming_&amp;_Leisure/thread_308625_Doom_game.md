---
title: "Doom game?"
date: 2006-11-28
forum: Gaming &amp; Leisure
---

### Post by dmb83fan41 on 2006-11-28
[COLOR="SeaGreen"]Hello all.  I am still a newbie to Ubuntu and everything that comes with it.  I was wondering where I could get a version of the original Doom to play on Ubuntu.  I would also need help installing it since I have no idea how to open and install files from the terminal.  I'm still learning all I can about  Ubuntu.  So far I love it so much more than XP!  Thanks for any help guys! [/COLOR]

---

### Post by pay on 2006-11-28
The engine of the game is opensource and can be compilled for Linux but you will still need the commercial cd of the game.

---

### Post by pay on 2006-11-28
You could try freedoom though [http://freedoom.sourceforge.net/about/](http://freedoom.sourceforge.net/about/)

---

### Post by pay on 2006-11-28
Actually, I found the files needed to play it that were released by idsoftware. [http://distfiles.gentoo.org/distfiles/doom1.wad.bz2](http://distfiles.gentoo.org/distfiles/doom1.wad.bz2) But thats only a shareware version of the first episode.

---

### Post by dmb83fan41 on 2006-11-28
Ok, I downloaded that and extracted it to the desktop.  Of course I have no idea what to do next with it.  It saved it as a .wad file.  Thanks for the help again!

---

### Post by pay on 2006-11-28
Thats the levels, now you need an engine to run the game. try this one ```
sudo aptitude install prboom
```if your running edgy an have the universe repository enabled. Now copy the .wad to /usr/local/share/games/doom/ (i think)```
sudo *.wad /usr/local/share/games/doom/
``` and then type in prboom. I don't have edgy installed (I use Gentoo) so I can't test if that method works or not

---

### Post by CowzRule on 2006-11-28
What version of Ubuntu are you using? 
Do you know how to add repositories to your "sources.list"?


P.S. Sent you a PM

---

### Post by geoffm33 on 2006-11-28
> **pay said:**
> Thats the levels, now you need an engine to run the game. try this one ```
sudo aptitude install prboom
```if your running edgy an have the universe repository enabled. Now copy the .wad to /usr/local/share/games/doom/ (i think)```
sudo *.wad /usr/local/share/games/doom/
``` and then type in prboom. I don't have edgy installed (I use Gentoo) so I can't test if that method works or not

I think you meant 

```
sudo **cp** *.wad /usr/local/share/games/doom/
```

---

### Post by pay on 2006-11-28
yeah thats what I meant. You might need to create the directory first though```
sudo mkdir /usr/local/share/games/doom/
```

---

### Post by CowzRule on 2006-11-28
This assumes you got my PM
Add one of the following to your sources.list```
sudo gedit etc/apt/sources.list
```For Edgy```
## Doom
deb http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
```For Dapper```
## Doom
deb http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse
```Save and close.
Get the key. In the terminal type```
gpg --recv-keys 0x4B6E7209
gpg --export -a 0x4B6E7209 > Yagisan.asc
sudo apt-key add Yagisan.asc
```Do ```
sudo apt-get update
```Now get```
sudo aptitude install deng deng-iwad-doomu-installer deng-iwad-doom2-installer deng-iwad-plutonia-installer deng-iwad-tnt-installer
```Keep an eye on the terminal. At some point it's going to ask you where the .wad files are. Just type in the location of the wad it's asking for. i.e. it's asking for "doomu.wad", just type "/home/name/doomu.wad" then hit enter.
Once it's finished, look in your "Games" menu for the launchers. You might have to do ```
killall gnome-panel
```to refresh the menus to see them.
Now open "Synaptic Package Manager" and do a search for "deng". You'll see all kinds of extra goodies for Doom. I would recommend installing these> deng-jdoom-rp-core
deng-jdoom-rp-decorations
deng-jdoom-rp-effects
deng-jdoom-rp-hud
deng-jdoom-rp-items
deng-jdoom-rp-monsters
deng-jdoom-rp-projectiles
deng-jdoom-ep
deng-jdoom-ui
deng-jdoom-tpNow enjoy Doom like you've never seen it before :)

---

### Post by OttifantSir on 2006-12-06
I love Doom, and even though this is a seven year old laptop, the original game (shareware version) ran fine on a 386 once upon a time, so it should work on this too. My question is: Is this the original game? Do I need to pay for it? (If so, I'll wait until I have gotten a new laptop in about three months time)
Will it run full-screen?

Thanks in advance for any help.

---

