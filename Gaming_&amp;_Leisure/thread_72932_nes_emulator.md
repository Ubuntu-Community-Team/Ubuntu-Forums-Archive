---
title: "nes emulator"
date: 2005-10-07
forum: Gaming &amp; Leisure
---

### Post by acejones on 2005-10-07
i've got a bunch of nes games.  i'd like to be able to play them legally in ubuntu, but i'm having problems finding an emulator and roms.  any help?

---

### Post by aysiu on 2005-10-07
zsnes is in Synaptic (you may have to enable extra repositories). If you don't know how to use Synaptic, see the second link in my sig. If you need extra repositories, follow these instructions:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

(don't put in the backports, though)

---

### Post by acejones on 2005-10-07
cool.  got zsnes, but the rom i downloaded is a .nes file and zsnes didn't read it.  what extension am i looking for?

---

### Post by smack on 2005-10-07
z'snes' ? Does that do nes?

---

### Post by kerm on 2005-10-07
I think he wants to play the older 8-bit NES games not the SuperNES ones. Unless there has been a recent update, I don't think ZSNES plays the older 8-bit games.

**fceu** can though and it can be obtained by using 'apt-get'. But since developement on fceu has stopped you may want to try mednafen instead and it can emulate a lot of different systems.

[http://mednafen.fobby.net]("http://mednafen.fobby.net")]

---

### Post by BoyOfDestiny on 2005-10-07
I made a build of mednafen (a little behind the latest)

[http://www.safaribans.com/gpl/mednafen-0.3.2.tar.bz2](http://www.safaribans.com/gpl/mednafen-0.3.2.tar.bz2)
[http://www.safaribans.com/gpl/mednafen_0.3.2-1_i386.deb](http://www.safaribans.com/gpl/mednafen_0.3.2-1_i386.deb)

It's built in breezy with the 2.6.12 kernel, but might work for you.

Also, if you play some snes, which zsnes is for, I have a nice cvs build that can play star ocean and mario kart etc etc (that the one in the ubuntu repository can't/has trouble with since it's over 2 years old!)

---

### Post by irish rebel on 2005-10-09
Okay as long as you own the games use synaptic to get fceu I like it as a nes emulator, get yourroms from wherever it is you get them, and have fun, if you have sega roms use dgen as a emulator.Again thru synaptic ......

---

