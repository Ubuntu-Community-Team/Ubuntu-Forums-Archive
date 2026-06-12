---
title: "I neec help with TA Spring and SpringLobby"
date: 2010-02-10
forum: Gaming &amp; Leisure
---

### Post by Minipalmer on 2010-02-10
Hey all,

I'm trying to support Open Source Gaming by trying out the Spring project.

I've installed the SpringLobby and managed to get Balanced Annihilation and some maps loaded.

However, for some reason Spring Lobby can't really act for itself in my home folder. Every time I download something it gives me an error that I need to move the download file into a new folder in my .spring directory, so I have to manually do this everytime.

Though, this doesn't always work because sometimes things are downloaded automatically that Spring cannot place in my directory because new folders haven't been made for it.

Hard to explain, but do you catch my drift? Hoping for for some help.

Thanks in advance.

---

### Post by Melcar on 2010-02-10
Well, at least you got further than I did with Spring.  Damn lobby always crashes on me.

---

### Post by Minipalmer on 2010-02-10
Ouch, sorry to hear that. Are you on 9.10? I just installed it from the repos.

---

### Post by Melcar on 2010-02-10
Both from the repos and building from source.

---

### Post by Minipalmer on 2010-02-10
Well that's no good. But I still need some help! :)

---

### Post by Azu on 2010-02-11
sudo add-apt-repository ppa:spring/ppa
sudo apt-get install springlobby
mkdir ~/.spring/mods/
mkdir ~/.spring/maps/



Have fun

---

### Post by Minipalmer on 2010-02-11
> **Azu said:**
> sudo add-apt-repository ppa:spring/ppa
sudo apt-get install springlobby
mkdir ~/.spring/mods/
mkdir ~/.spring/maps/

Thanks for the reply. However, I've already done all of these things. It is still having trouble moving files around and making directories on its own for things like the game's AI. Permissions problem, perhaps?

---

### Post by Minipalmer on 2010-02-12
Bump.

I tried running a single player game with one bot (AAI 0.9). The game starts, units load, and then it says the game is over. It flashes a log saying that the AI is missing the BA711.cfg file.

Granted, I may be able to find this cfg file somewhere, but I can't keep manually installing files or else I'll never be able to keep up with any games in multiplayer that are constantly changing mods and such.

Help :(

---

### Post by Azu on 2010-02-12
I use RAI 0.601 when I play offline and it works fairly good.

---

### Post by yanom on 2010-07-20
HELP! I don't have a .spring directory! I accidentally deleted it, then reinstalled but it wont come back!

---

### Post by huwjenjinn on 2010-09-13
> **Azu said:**
> I use RAI 0.601 when I play offline and it works fairly good.

That's the only one I've had success with so far.

---

### Post by ELD on 2010-09-13
You have to create the maps, mods and AI etc etc folders yourself, for some odd reason the packages don't make those folders for you - that is why it gives the errors because it is trying to move to a directory that doesn't exist...

All they need to do is add something to make the folder if it doesn't exist - or create the folders on install...a known problem but they don't seem to want to fix it as it's not a big issue you only need to make folders..no biggy either way.

---

