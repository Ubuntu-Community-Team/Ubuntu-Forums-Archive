---
title: "Installing nethack - help :)"
date: 2008-03-19
forum: Gaming &amp; Leisure
---

### Post by Tyke91 on 2008-03-19
I'd like to install the original nethack from the website (not the new shiney one with "graphics") but I'm running into some problems.

[http://www.nethack.org/v343/ports/download-linux.html](http://www.nethack.org/v343/ports/download-linux.html)

they offer .rpm binaries and a tar.gz file. I've downloaded the tar, but I don't know what to do with this. it says to gunzip and untar into / using -p to keep permissions. but what are the commands? I know I should probably know them by now, but I have just never come across this situation before.

PS: will I be able to play this version of nethack in a shell environment? i.e no xserver. because I try to use the terminal as much as possible (to learn to use it better :D ) and it would be a bonus to be able to play a game without the gui.

---

### Post by Izkata on 2008-03-19
The no-gui version is available in the repositories - I don't remember it's exact name, though.

I think I found it by doing "apt-get install nethack", and it told me to choose which version.

---

### Post by binarymutant on 2008-03-19
just do this in a terminal:

sudo apt-get install nethack-console

or you can use the Synaptic Package Manager to install it. Great game but I can't get very far in it :)

---

### Post by Tyke91 on 2008-03-20
cool :) I had no clue that was in there... I thought it was only gnome-nethack

---

### Post by Seren on 2008-03-20
You can also play nethack online with telnet on the excellent [http://nethack.alt.org](http://nethack.alt.org)

The site was down a few days ago but it seems to be back.

There is some interesting statistics recorded. You can get help from more experienced players on the server channel ( #nethack on irc.freenode.org).

---

