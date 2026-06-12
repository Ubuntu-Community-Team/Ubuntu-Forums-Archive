---
title: "Toadeki - v0.0.1a"
date: 2013-11-26
forum: Gaming &amp; Leisure
---

### Post by slooksterpsv on 2013-11-26
Hello Everyone,

I'm working on a game in C++ and SDL to push the limits of my programming knowledge and to use my coding skills and make a bigger project. I want to make sure this program runs on other's computers though as I'm working on it in Ubuntu (well Elementary OS Luna). If you guys could just see if it opens, if you can move, or if it gives you any errors, that'd be great. There's not much to this other than some heart containers in the top left, a sprite moving around the screen, and a map (which you can edit). It's a work in progress and I've been working on this for about 5 hours a day. Any comments suggestions, etc. would be appreciated:

Movement:
UP, DOWN, LEFT, RIGHT

Other actions:
Space to deplete heart containers.

If you just want to see Toadeki view my Youtube video of it - [https://www.youtube.com/watch?v=pt7NtiBDDBU](https://www.youtube.com/watch?v=pt7NtiBDDBU)

Thanks,



Shawn[ATTACH]248100[/ATTACH][ATTACH=CONFIG]248101[/ATTACH]

---

### Post by slooksterpsv on 2013-12-02
Here's some new screenshots.

I have started to implement an editor and I've implemented an enemy (no movement AI yet), but I'm planning on doing a radial AI meaning of the enemy and player fall into the same diameter the enemy runs towards the player.

Enjoy, if you guys want to try I'll submit another tar.gz file for you guys to test out.[ATTACH=CONFIG]248258[/ATTACH][ATTACH=CONFIG]248259[/ATTACH][ATTACH=CONFIG]248263[/ATTACH]

---

### Post by slooksterpsv on 2013-12-12
Alrighty I have a new release, just want to see how the code handles on other machines. I'm guessing I have memory leaks in it as I'm not freeing up all surfaces as needed - this will be fixed soon, but here's the leaky version for now.

I've implemented a map editor so that you can edit the current map. I don't have switching maps, movable npcs, other enemies, or a way to attack and have it hit besides facing to the right.

e opens map editor
q quits map editor
1 and 2 increment and decrement the map tile to place, respectively

3 and 4 increment and decrement the map tile type - 2 is cannot move though

Let me know what you guys think:

[ATTACH]248557[/ATTACH]

---

### Post by slooksterpsv on 2014-01-16
I'm attempting to make this game cross platform so I decided to work on the Windows version, bad part is the code does not translate that well. Ugh it's been a nightmare, but I decided to reprogram it in SDL2. I have just the very basics and I've reworked some of the code so no moving sprites yet, just an intro, main menu, and when you start new game it just shows hearts. It's a WIP I've been working on this portion for about 6 hours today. Here's the Windows variant. Let me know what you think.

[https://drive.google.com/file/d/0BzvZWf6CGx93OTBnaHB5UXRPLUE/edit?usp=sharing](https://drive.google.com/file/d/0BzvZWf6CGx93OTBnaHB5UXRPLUE/edit?usp=sharing)

There ya go

---

### Post by slooksterpsv on 2014-02-09
[https://drive.google.com/file/d/0BzvZWf6CGx93d29XenM3WktfYjQ/edit?usp=sharing](https://drive.google.com/file/d/0BzvZWf6CGx93d29XenM3WktfYjQ/edit?usp=sharing)

New windows version. Sorry it's not Linux version; I need to wait until April for 14.04 to come out as i have lots of issues with 12.04.

---

### Post by sffvba[e0rt on 2014-02-09
My apologies for only seeing this thread now.  Best of luck with your project (can't promise I will play this but if time permits I will give it a go)...

---

### Post by HeartlessContrapti on 2014-02-09
Upon attempting to launch the 0.2a version on Ubuntu 12, I get an invalid encoding error file that pops up in the game directory, without the game launching. I'm going to attempt to launch the windows version in WINE and I'll report back.
----EDIT------
Downloaded the windows version from your Drive and found nothing in the .rar archive.

---

### Post by slooksterpsv on 2014-02-11
I think when I made the rar archive I did it as RAR5; do the rar commands in Ubuntu support RAR5? I'll change it to a zip as that'll be easier to handle.

[https://drive.google.com/file/d/0BzvZWf6CGx93MGxVMktxQzNxTnM/edit?usp=sharing](https://drive.google.com/file/d/0BzvZWf6CGx93MGxVMktxQzNxTnM/edit?usp=sharing)

---

### Post by slooksterpsv on 2014-02-24
[SIZE=5]**_Linux Version_**[/SIZE]

[https://drive.google.com/file/d/0BzvZWf6CGx93VlREVUh4R1VLa1U/edit?usp=sharing](https://drive.google.com/file/d/0BzvZWf6CGx93VlREVUh4R1VLa1U/edit?usp=sharing)

!!!! WARNING !!!!
=============
Yes there are memory leaks in the program and I know where they are at. A few of the textures never get destroyed/released back into memory. I'm not sure what this does after the program's done, but I'm guessing a restart should fix that.
=============

New version of Toadeki is up, here's the new items:

1. Requires SDL2 - Once the game is done I'll port it to SDL 1.2 for backwards compatibility.
2. More than 1 map (ok... 2) - I'm working on Warp Points and coding files with warp points, it'll take some time
3. A weapon - You can throw a rock with the m key - this is not going to be the default key as it's for testing purposes
4. Bounding Box Collision - bounding box collision for all tiles, even if you throw  a rock.
5. A moving bush - yes there is a moving bush, I'm working on enemy AI so if you see a bush wandering around, give it a few more releases to get that down.

What I need still:

Graphics - better graphics
Sounds - not going to be implemented until the end, but may be useful to start looking for what I would like
Animations - character, enemy, etc. animations, preferably in a tileset

That's all I need for now, try it out, 

Let me know of any bugs, cryptic errors, etc. The most common one should be that SDL2 looks for an accelerated driver. I will look into software mode execution, but if not I'll port it to SDL 1.2 after it's finished.

---

### Post by slooksterpsv on 2014-02-27
This thread is dead, I'm creating a new one, if a mod could move this thread, that'd be great. Thanks!

---

