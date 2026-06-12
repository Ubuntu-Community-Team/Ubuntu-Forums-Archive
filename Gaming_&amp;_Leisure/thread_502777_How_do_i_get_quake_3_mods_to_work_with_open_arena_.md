---
title: "How do i get quake 3 mods to work with open arena - or any mod for that matter?"
date: 2007-07-17
forum: Gaming &amp; Leisure
---

### Post by Slyth99 on 2007-07-17
Hi,

just wondering if anyone knows much about open arena - i downloaded it from get deb for dapper. I wondering about running mods for quake 3 with this game - any suggestions?

---

### Post by cmat on 2007-07-17
I believe you cannot since it's stated on the website that it is not compatible with Quake 3.

EDIT: I stand corrected [http://openarena.wikia.com/wiki/ModCompat](http://openarena.wikia.com/wiki/ModCompat)

---

### Post by Slyth99 on 2007-07-17
Do you know of a website that has any open arena single player campaigns?

---

### Post by hikaricore on 2007-07-17
The only single player mode for the game includes local bots.

This may change in the future but for now that's how it is.

---

### Post by johnny4north on 2007-07-17
Quake 2 is a single player game heres link  - [https://help.ubuntu.com/community/Games/Native/Quake2](https://help.ubuntu.com/community/Games/Native/Quake2)
thanks cmat for the link to the online manual - [http://openarena.wikia.com/wiki/FAQ#I_have_no_3D_card_.2F_No_OpenGL_acceleration_.21](http://openarena.wikia.com/wiki/FAQ#I_have_no_3D_card_.2F_No_OpenGL_acceleration_.21) 
is it that easy to add a mod to Open arena? >  The installation is nearly the same as in Q3A. Simply copy the .pk3 files (of the map/model/etc) in your OpenArena/baseoa/ directory.  Mods need a subfolder at OpenArena/ instead of "Quake 3 Arena/". 

---

### Post by dmn_clown on 2007-07-17
As johnny4north said:

Install the mod the same way you would on q3a:

extract the file in the same directory that baseoa resides in for system wide install, otherwise you can install the mod in ~.openarena/ and choose to start the mod from either the mods menu or from the commandline like so: ```
./ioquake3.x +set fs_game your_spectacular_mod
``` where x is your architecture.

For server side only mods (such as instagib, unlagged, etc.) the setup is different as the modded VM's need to go into the vm directory and not in their usual place.

---

### Post by Slyth99 on 2007-07-17
Thanks for all your help guys!

The mod I am going to try is excessive plus.

I am currently also checking out downloading quake 2 - does the demo version enable you to play mods?

---

### Post by MilesTeg on 2007-07-19
sorry, all demo-versions of games I know of don't legally support mods :(

There is one singleplayermod called sidrial, but it never got completed. If I remember right the game works with OA except for a few texture errors.

I'm currently working on a program that makes it even easier to get and start mods and other content for openarena.

---

### Post by weblordpepe on 2007-07-19
> **MilesTeg said:**
> sorry, all demo-versions of games I know of don't legally support mods :(

There is one singleplayermod called sidrial, but it never got completed. If I remember right the game works with OA except for a few texture errors.

I'm currently working on a program that makes it even easier to get and start mods and other content for openarena.Cool!

---

