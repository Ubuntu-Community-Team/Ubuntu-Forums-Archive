---
title: "Opensource Loderunner for Linux ?"
date: 2008-05-12
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-05-12
Hello,

We are looking for a opensource Loderunner for Linux, ie:
[http://www.pcgaming.ws/screenshots/loderunner.gif](http://www.pcgaming.ws/screenshots/loderunner.gif)
 
In better or the same is enough
Is there that for linux (no wine) ?
thx

---

### Post by frenchn00b on 2008-05-12
There is : 
kgoldrunner  which is great 
and xscavenger


the problem with kgoldrunner , is that he keeps running even if you release keyboard arrows

---

### Post by badactress on 2008-05-12
from the screenshots, maybe holotz-castle? It's a fantastic game! in the repos too if you search for it..

---

### Post by frenchn00b on 2008-05-12
> **badactress said:**
> from the screenshots, maybe holotz-castle? It's a fantastic game! in the repos too if you search for it..

I have found this solution : 

download of meka for linux 0.70
and then got the master system Loderunner :)
that's a way like 
  
TO7 had a great one of loderunner, but I cannot find the cardrige m7 :(

---

### Post by anjilslaire on 2008-05-12
> **frenchn00b said:**
> There is : 
kgoldrunner  which is great 
and xscavenger


the problem with kgoldrunner , is that he keeps running even if you release keyboard arrows

Agreed. Kgoldrunner is awesome. In the repo's

---

### Post by donkyhotay on 2008-05-13
I play xscavenger when I need to satiate my love of lode runner

---

### Post by acoustibop on 2008-05-13
> **frenchn00b said:**
> I have found this solution : 

download of meka for linux 0.70... (

You obviously haven't tried getting Mekanix (the proper name for the Linux version of Meka) working, frenchn00b.  It used to be my Master System emulator of choice in Windows, but in Linux...

Try [Mednafen]("http://mednafen.sourceforge.net/") instead.  Version 0.8.8 emulates Master System games excellently, and the bug that prevented the Pause button from working is fixed.  You can get a .deb for version 0.8.8 that FranMichaels very thoughtfully posted [here]("http://ubuntuforums.org/showpost.php?p=4655351&postcount=26").

---

### Post by Frem on 2008-05-15
> **frenchn00b said:**
> the problem with kgoldrunner , is that he keeps running even if you release keyboard arrowsThis is accurate to the original game, I believe.

> **frenchn00b said:**
> I have found this solution : 

download of meka for linux 0.70
and then got the master system Loderunner :)You wanted an open source version, yet you're emulating it. Bwa?

You did say "No Wine", but "Lode Runner Online: Mad Monk's Revenge" was released for free by the lead developer. I feel compelled to mention it as a ligit alternative to emulating SMS roms you probably don't own. ;-)

[http://www.daggert.net/Folio/Programming/Presage/LodeRunner/Loderunner1.htm](http://www.daggert.net/Folio/Programming/Presage/LodeRunner/Loderunner1.htm)

---

### Post by eFFeeMMe on 2008-05-15
[http://www.pygame.org/project/424/](http://www.pygame.org/project/424/)

Maybe this one, written in python, will do?

---

### Post by frenchn00b on 2008-05-18
> **eFFeeMMe said:**
> [http://www.pygame.org/project/424/](http://www.pygame.org/project/424/)

Maybe this one, written in python, will do?

Indeed, this one is very great, thanks ! : 

```
#!/bin/bash
sudo apt-get install python-pygame  python-opengl
cd /tmp ; wget -k http://www.psyguygames.com/loderunner07.tar.gz
tar xvf loderunner07.tar.gz
cd loderunner07/
python loderunner.py
```
  
but it still lacks of reactivity. I think the very best lode runner was the one of the Thomson T07, but we cant find the "rom" / program anymore.

---

### Post by Ferk on 2008-08-26
I'm also wanting for this!

> **frenchn00b said:**
>   
but it still lacks of reactivity. I think the very best lode runner was the one of the Thomson T07, but we cant find the "rom" / program anymore.


Maybe suggestions can be given in the page of the python project. 
I really think a good free sourced lode runner clone is needed. And emulating a closed source one is not a solution, nor using KDE specific libraries for a game.
What are the things you think would improve it? any ideas for new objects and terrains?

---

### Post by Ferk on 2008-08-26
oh! there's also a new version of scavenger, made in SDL with some improvements over xscavenger ^^
[http://sourceforge.net/projects/sdlscavenger/](http://sourceforge.net/projects/sdlscavenger/)

---

