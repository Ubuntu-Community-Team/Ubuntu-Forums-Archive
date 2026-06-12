---
title: "ActionCube Freeze"
date: 2007-04-09
forum: Gaming &amp; Leisure
---

### Post by racoq on 2007-04-09
Hello friend gamers, i am a recent gamer in Linux.  I have installed Xubuntu Feisty, Beta Version, and since that i'm an adept of native games, i've download a few games, like ActionCube, Cube 2, Tremelous, etc...

For ActionCube i have downloaded the oficial tar.bz2, archive available at:

[http://downloads.sourceforge.net/actiongame/ActionCube_v0.92.tar.bz2?use_mirror=switch]("http://downloads.sourceforge.net/actiongame/ActionCube_v0.92.tar.bz2?use_mirror=switch")

I have untared and the game works ok, really smooth,  however it constantly freezes, and i have to do an Ctrl + Alt  + Backspace to do a new session restart, and launch the game.  The Freezes are random, i can play 30 minutes without freeze, or can only play 10 or 5 minutes before that happens.
The game uses libsdl-image, libsdl-mixer, and libpng, i suspect that one of the errors is at one of  the Ubuntu library's.
I also play quite often Cube 2, and after say..., 1 hour of playing it also blocks. So i suspect since both use Libsd for graphics that the library that the beta version that comes with feisty beta is buggy.

My Hardwware Specs are:

Pentium III 800
512 MB SDRam 133
Nvidia Geforce 4 TI4200 with 64MB DDR
and running Nvidia proprietary Drivers

I was wondering if this is a bug and if i should report  it in  launchpad, or anyone has had similar problems and found a solution for this.

Some help / feedback here would be important

---

### Post by racoq on 2007-04-10
Bump

---

### Post by Odrodzona-Sarmacja on 2008-07-07
Hi!

I have exactly the same freezes due the same bug, although I am on Xubuntu 8.04 (Hardy) myself. I found out that you can play for extended periods of time on Hardy after purging network-manager and going offline.
[http://ubuntuforums.org/showthread.php?t=840686](http://ubuntuforums.org/showthread.php?t=840686)

Did you try downgrading to earlier versions ([http://packages.ubuntu.com/](http://packages.ubuntu.com/)) of libsdl and libpng packages?

---

