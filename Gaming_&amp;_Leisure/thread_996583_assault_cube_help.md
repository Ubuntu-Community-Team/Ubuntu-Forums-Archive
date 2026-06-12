---
title: "assault cube help"
date: 2008-11-29
forum: Gaming &amp; Leisure
---

### Post by seventstrat on 2008-11-29
Hey everyone,

I installed assault cube via AI's guide

[http://gaming.gwos.org/doku.php/guides:64bit:assultcube](http://gaming.gwos.org/doku.php/guides:64bit:assultcube)

but it would not run. I then found a link to the .deb files on getdeb.net, but I'm pretty sure it was an older version. So now I have the v1.0 that I installed via AI's guide (which doesn't load) and I have the .93 version that does load but nobody uses....

So i guess my question is, how do I uninstall all this garbage and set it up right? Or, is there a better game for ubuntu I should be checking out =)

I'm a noob to linux, but I'm pretty good at copying and pasting code into the terminal haha, any help is appreciated

thanks

---

### Post by Perfect Storm on 2008-11-29
It would help if you tell us what's not working.

If you still have the one the guide show do;
```
sh -c "cd ~/.Games/AssaultCube_v1.0 && sh assaultcube.sh"
```
and see what it says.
If the .deb didn't work either it may be completly diffrent problem (video card?)

---

### Post by seventstrat on 2008-11-29
Sorry AI, I was not specific enough. Basically I installed assault cube v1.0 via your guide, and it simply would not open. Nothing happened when I would try to open it. Then, I searched threads in this forum and they kept mentioning to search for a deb file on getdeb.net. I could not find one for assault cube, however, I found a link to one in another thread and downloaded / installed it. This installed a new version of assaultcube, and runs. However, I beleive this is the .93 version, not version 1.0

my question is, how do I delete this .93 version, and how do I get the v1.0 to run? It can't be my gfx card, because .93 ran flawlessly, just that there weren't many available servers (obviously, due to the old version of the game)


I put what you said into the terminal and it came back with this message:

.//bin_unix/linux_client: error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory


I'm wondering if this has to do with the conflict of having 2 versions of the game probably installed in the same location?

---

### Post by Perfect Storm on 2008-11-29
You can uninstall the .deb of Assault Cube via Synaptic Package Manager (system ---> Administration ---> Synaptic)


> .//bin_unix/linux_client: error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory

I assume you're using Ubuntu 8.10;

```

sudo apt-get install libopenal1
```

---

### Post by seventstrat on 2008-11-29
excellent. I didn't know you could use synaptic package manager to uninstall packages too! So i successfully got rid of the .93 version and v1.0 works fine

thanks alot AI.

on a side note, any other games for ubuntu you'd reccomend?

---

### Post by Perfect Storm on 2008-11-29
Only .deb package you manual installed or through Ubuntus repo.

> on a side note, any other games for ubuntu you'd reccomend?
It really depends which genre and if it's "Commercial", freeware or Open Source you're looking for.

---

### Post by seventstrat on 2008-11-29
I guess the genre would be FPS, I assume commericial you pay for (they have those?) and freeware/OS are free, right? I guess if it looked like a good game I'd buy it

---

### Post by Perfect Storm on 2008-11-29
FPS, ok. Yep, commercial = pay + close source. Freeware = no pay + close source. Open Source = can cost money + Open Source but most unlikely.


There's good FPS out there for Linux; Those I personaly find interesting;

Open Source;
[Alien Arena](http://gaming.gwos.org/doku.php/games:alphabetical:a:alienarena)
[Cube 2: Sauerbraten](http://gaming.gwos.org/doku.php/games:alphabetical:c:cube)
[Wolfenstein: Enemy territory](http://gaming.gwos.org/doku.php/games:alphabetical:c:cube)
[Nexuiz](http://gaming.gwos.org/doku.php/games:alphabetical:n:nexuiz)
[Open Arena](http://gaming.gwos.org/doku.php/games:alphabetical:o:open_arena)
[Transfusion](http://gaming.gwos.org/doku.php/games:alphabetical:t:transfusion)
[Urban Terror](http://gaming.gwos.org/doku.php/games:alphabetical:t:transfusion)
[Warsow](http://gaming.gwos.org/doku.php/games:alphabetical:w:warsow)
[World of Padman](http://gaming.gwos.org/doku.php/games:alphabetical:w:world_of_padman)

Commercial;

[Quakewars](http://gaming.gwos.org/doku.php/games:alphabetical:e:etqw)
[Postal 2: Share the Pain](http://gaming.gwos.org/doku.php/games:alphabetical:p:postal_2_share_the_pain)
[UT2004](http://gaming.gwos.org/doku.php/games:alphabetical:u:unreal_tournament_2004)
...and [Prey](http://gaming.gwos.org/doku.php/games:alphabetical:p:prey) is comming soon.
With UT2004 there's alot of cool totally conversion mods.

---

### Post by seventstrat on 2008-11-29
cool deal, I installed nexuiz which is sweet (apt-get install nexuiz), however whenever I exit the game freezes on me. I have read this has to do with the ATI drivers, that's pretty disappointing. I also was checking out alien arena, downloaded it, extracted it like your guide said to (swapping out 2007 for 2008) and then past that point I couldn't figure out what to do.

[http://gaming.gwos.org/doku.php/guides:32bit:alienarena](http://gaming.gwos.org/doku.php/guides:32bit:alienarena)

I followed this guide, and I changed : 

nano ~/.Games/alienarena2007/Launch-AlienArena.sh

to

nano ~/.Games/alienarena2008/Launch-AlienArena.sh


copied and pasted the code for the .sh, changed 2007 to 2008, and it said it couldn't save it because it did not exist.


Do you have any ideas for either alien arena or why I cannot exit Nexius w/o freezing?

I'm running ubuntu 8.10, an ati firegl gfx card, core2 duo 2ghz, 2gb ram, 32bit ubuntu

---

