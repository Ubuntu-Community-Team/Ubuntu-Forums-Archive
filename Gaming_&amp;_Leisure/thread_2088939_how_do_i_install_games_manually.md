---
title: "how do i install games manually??"
date: 2012-11-27
forum: Gaming &amp; Leisure
---

### Post by csmcpb on 2012-11-27
hi all 
I am very new to linux and have gone with ubuntu 12.04 as my distro. I have been trying to install greedy car thieves and gameplay football which as far as im aware have to be installed manually, i have downloaded both games and unzipped them, made them excutable but when i click on the excutable literally nothing happens, no error message and does not install. Am i missing a step? or have i just been to pampered by windows?!

---

### Post by ibjsb4 on 2012-11-27
Are these linux games or do you need wine to run them?

There's usually a "read me" file that comes with such packages.

Give us the download links

---

### Post by csmcpb on 2012-11-27
no wine is not needed they are native. i did read the readme files and followed instructions as best i could but i must be doing something wrong!
 
 [http://www.indiedb.com/games/gameplay-football/downloads](http://www.indiedb.com/games/gameplay-football/downloads) gameplay football
 
 
 
i cannot find the link for greedy car theives now as the developer seems to have taken it off of their website since yesterday for linux!

---

### Post by ibjsb4 on 2012-11-27
Ok as far as Im concern, not going to happen.

First line in the read me file:

"- if you don't have them already, you need to install SDL, SDL_ttf and SDL_image"

This is RPM (like RedHat) or OSX (Apple).  No package for Ubuntu (.deb) unless you build it from source.

[http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php)

Sorry

There is a Ubuntu sub forum for games.  Maybe post there a ask about football (soccer) games for Ubuntu.

Edit:  sorry, just realized that this is the gaming forum  :)

---

### Post by csmcpb on 2012-11-27
oh i see! shows how new i am didnt realise that at all! thank you for your help, much appreciated! :)

---

### Post by Toz on 2012-11-27
Actually, the sdl packages do exist in the ubuntu repositories. Do a search in software centre for **libsdl**.

I don't have access to a 12.04 install right now, but in 12.10, they appear to be called:
- libsdl1.2debian
- libsdl-ttf2.0-0
- libsdl-image1.2

EDIT: Just tested it here and it works fine with those 3 packages installed.

---

### Post by ibjsb4 on 2012-11-27
> **Toz said:**
> Actually, the sdl packages do exist in the ubuntu repositories. Do a search in software centre for **libsdl**.

I don't have access to a 12.04 install right now, but in 12.10, they appear to be called:
- libsdl1.2debian
- libsdl-ttf2.0-0
- libsdl-image1.2

EDIT: Just tested it here and it works fine with those 3 packages installed.

Nice find Toz; guess this is why you get paid the big bucks  :)

---

### Post by csmcpb on 2012-11-27
thanks toz i shall give that a go when i get off my night shift!
 
as i said im a complete noob with regards to linux, after i have installed the 3 files is it just a case of giving the gameplay football file permission to be excutable and the game installs from there?

---

### Post by Toz on 2012-11-27
> **csmcpb said:**
> after i have installed the 3 files is it just a case of giving the gameplay football file permission to be excutable and the game installs from there?

It looks like it already has the executable bit set, so you can just double-click it to start it.

---

