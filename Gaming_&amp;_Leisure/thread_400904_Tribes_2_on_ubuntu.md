---
title: "Tribes 2 on ubuntu"
date: 2007-04-04
forum: Gaming &amp; Leisure
---

### Post by moot on 2007-04-04
I used to play Tribes 2 a few years back on Windows XP and found out that Vivendi now lets you download both the 1st and 2nd games for free and that there was a Linux port for Tribes 2.  What I want to know is how exactly do I go about running Tribes 2 natively on Ubuntu?  I found this link on Fileshack:

[http://www.fileshack.com/file.x/1201/Tribes+2+Linux+v25026+Full+Update](http://www.fileshack.com/file.x/1201/Tribes+2+Linux+v25026+Full+Update)

But I'm not sure if that will work, does anyone have a link to download the latest Linux version of Tribes 2 along with the patch?  I also found the link to the Windows download, but I don't want to use Wine if I don't have to.

---

### Post by Perfect Storm on 2007-04-04
sudo sh XXXXXXXXXXX.run should do it, just exit the installer afterwards to avoid permission conflict.

---

### Post by moot on 2007-04-04
> **Artificial Intelligence said:**
> sudo sh XXXXXXXXXXX.run should do it, just exit the installer afterwards to avoid permission conflict.


As I feared, the link might just be the patch and not the actual game, I got an error when I executed the file:

```
Verifying archive integrity...OK
Uncompressing Tribes 2 2Verifying archive integrity...OK
Uncompressing Tribes 2 25026 Update............................................. ................................................................................ .
loki_patch: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic t ag"' failed.
./update.sh: line 60: 15761 Aborted                 loki_patch --verify patch.da t
The program returned an error code (1)
5026 Update............................................. ................................................................................ .
loki_patch: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic t ag"' failed.
./update.sh: line 60: 15761 Aborted                 loki_patch --verify patch.da t
The program returned an error code (1)
```


Edit: It turns out that it was just a patch, does anyone know where I can download the Linux version of Tribes 2?

Edit2: Not only was it just a patch, but an old patch at that <_<, this is the latest one:

[http://www.fileshack.com/file.x/1685/Tribes+2+v25034+Full+Patch+-+Linux](http://www.fileshack.com/file.x/1685/Tribes+2+v25034+Full+Patch+-+Linux)

Also, after checking isohunt I couldn't find the Linux version of Tribes 2, just some stuff relating to Tribes 3, the word tribe and a Windows Tribes 2 Demo crack.

---

### Post by ndefontenay on 2007-04-04
Tribes 2! That's great.

It should be on the official web site I think. If it's not there I don't see how we could get it.

I'll try tonight. That's such a great news!

---

### Post by moot on 2007-04-04
I found the original announcement on GameSpy:

[http://pc.gamespy.com/pc/tribes-2/505494p1.html](http://pc.gamespy.com/pc/tribes-2/505494p1.html)

They must have only re-released the Windows version for free or something, because that's all I see on Fileplanet.

---

### Post by Perfect Storm on 2007-04-04
See if you can find a cheap copy of the game which have the linux version on it, it could be an option (eg. Ebay). Loki (those who ported Tribes 2 to Linux) do not exist anymore.

---

### Post by M_the_C on 2007-04-04
The free version is no longer available.  [Link.]("http://en.wikipedia.org/wiki/Tribes_2#Legacy")

---

### Post by compiledkernel on 2007-04-04
Sadly as a professedly large Tribes 2 player (my clan was TWL top 10 on the arena circuit for a few months) I found the re release to be a really cool deal. What I found out was though 

1. They didnt release the Loki installer from loki games
2. They only released the windows version 
3. You have to patch the system in a funky way to avert the Sierra update crap 
4. If you wanted to register a new account you had a certain number of days. They stopped the new account registration crap almost 3 days after the re release, so unless you have an old accont like I do, you cant actually get the game running properly. 

All in all, if none of the above impedes you, its just easier to get a copy of ebay for 5 bucks or whatever, and install it using wine. Loki's port of T2 was a joke.

---

