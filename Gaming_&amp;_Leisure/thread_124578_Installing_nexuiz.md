---
title: "Installing nexuiz"
date: 2006-02-01
forum: Gaming &amp; Leisure
---

### Post by shade11 on 2006-02-01
I wanted to play some sort of highly graphical FPS game with Ubuntu. I found Nexiuz! But I don't know how to install it. I tried

chmod -x nexuiz_1.2.1-english.run
sudo nexuiz_1.2.1-english.run

and also "Run in Terminal"ed it.

It comes out with this error message:
```

Verifying archive integrity... All good.
Uncompressing Nexuiz 1.2.1-english Installer...................................................................Extraction failed.
.Signal caught, cleaning up
```


I really want to play this game. But I don't know how to install it. I would have got it off Synaptic but it is not there. Please help!

---

### Post by jaakan on 2006-02-25
just download it, unzip it, and run it 

I unzipped it in to my home dir.
I open a Terminal window and cd to the /nexuiz
first chmod u+x nexuiz-linux*
then 
./nexuiz-linux-x86_64-sdl
or 
./nexuiz-linux-686-sdl

or to run a 64bit game server
./nexuiz-linux-x86_64-dedicated


Current version is 1.5 [http://www.nexuiz.com/]("http://www.nexuiz.com/")


[QUOTE=shade11]I wanted to play some sort of highly graphical FPS game with Ubuntu. I found Nexiuz! But I don't know how to install it. I tried

chmod -x nexuiz_1.2.1-english.run
sudo nexuiz_1.2.1-english.run

and also "Run in Terminal"ed it.

It comes out with this error message:
```

Verifying archive integrity... All good.
Uncompressing Nexuiz 1.2.1-english Installer...................................................................Extraction failed.
.Signal caught, cleaning up
```


I really want to play this game. But I don't know how to install it. I would have got it off Synaptic but it is not there. Please help![/QUOTE]

---

### Post by swatto on 2008-02-23
Hi all

I also can't get this to install/run - did what you said on the above post but this error came up:

**bash: ./nexuiz-linux-x86_64-sdl: cannot execute binary file**

Any help would be appreciated,

cheers :)

---

### Post by mivo on 2008-02-23
It's an old thread, and by now Nexuiz has been added to the repository. Did you try to install it via Synaptic, Swatto?

---

### Post by Perfect Storm on 2008-02-23
Old thread - please read the sticky that says Ubuntu 64-bit gaming guides.
Also - [http://gaming.gwos.org/doku.php/games:alphabetical:n:nexuiz](http://gaming.gwos.org/doku.php/games:alphabetical:n:nexuiz)


Thread closed.

---

