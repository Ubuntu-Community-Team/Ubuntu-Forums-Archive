---
title: "Garry's Mod (Source Engine?) Issues with OpenGL"
date: 2016-02-20
forum: Gaming &amp; Leisure
---

### Post by Burgy on 2016-02-20
Really recent install of Xubuntu 14.04 and I was trying to test out what this computer could run so I wanted to try out Garry's Mod and I received this error:
[ATTACH=CONFIG]267401[/ATTACH]

Is this a hardware issue or is there something I can do to resolve this? It used to run on Windows fairly fine.

lswh output: [http://pastebin.com/DEW37r4s](http://pastebin.com/DEW37r4s)

---

### Post by potato5 on 2016-02-20
> 
In the latest nvidia driver (361.28), nvidia began using a new vendor-neutral dispatch library for opengl.

As a result, some games will fail to start (e.g., many source engine games).

There are currently two fixes. One has performance concerns and one does not.

The preferred method:
In the launch options of the game, paste the following:
__GLVND_DISALLOW_PATCHING=1 %command%

If that fails to work, try pasting the following:
__GL_THREADED_OPTIMIZATIONS=0 %command%

Finally,  if *that* fails to work, find the launcher script of the game in  ~/.local/share/steam/steamapps/common/$game/. It should end in .sh.   Open the file in a text editor and see whether "  __GL_THREADED_OPTIMIZATIONS=1" is present; if it is, change it to "  __GL_THREADED_OPTIMIZATIONS=0"


[http://steamcommunity.com/app/221410/discussions/5/412447613567623129/](http://steamcommunity.com/app/221410/discussions/5/412447613567623129/)

---

### Post by Burgy on 2016-02-20
I'll try that when I'm home, thanks a ton.

---

### Post by Burgy on 2016-02-20
Sorry for the double post, those fixes didn't fix my issue. I am still getting the error message, but I noticed those fixes are for the latest nVidia drivers. I am running the nvidia-304 package since this computer is an old bastard that I'm trying to re-purpose a little for a friend.

[ATTACH=CONFIG]267411[/ATTACH][ATTACH=CONFIG]267412[/ATTACH]

---

### Post by potato5 on 2016-02-21
[https://github.com/ValveSoftware/Source-1-Games/issues/32#issuecomment-14117516](https://github.com/ValveSoftware/Source-1-Games/issues/32#issuecomment-14117516)
But not sure if it will help now.

---

