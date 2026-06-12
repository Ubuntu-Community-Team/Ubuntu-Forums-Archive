---
title: "Counter-Strike and opengl"
date: 2006-06-17
forum: Gaming &amp; Leisure
---

### Post by Dr_Deadmeat on 2006-06-17
Hello =)

I am going to a lan today, but I have problems getting Counter-Strike to work... It runs nicely in software mode except a couple of small hangups in the start, but else it works just as nicely as everything else.

My problem is that if I try to change the game from software acceleration to opengl acceleration it will crash giving me a error: "Pixel Format Failed" it have been there as long as I have tried, and it is very troublesome...

I run a laptop with 1,8ghz and nVidia geforce4 420go 16mb ram...

Hope you can help me =)

EDIT: I am using CS in wine by the way ;)

---

### Post by eqisow on 2006-06-17
CS in OpenGL shouldn't be a problem. Do you have 3D acceleration working? Do "glxinfo | grep direct" to find out. it should say, "direct rendering: Yes."

If it doesn't, try the [wiki for installing nVidia drivers]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia").

If you have 3D acceleration working, you could try running winecfg via the terminal, going to the graphics tab, then unchecking "Allow Pixel Shader."

Edit: If neither of those work, you could try changing the Windows version for Wine under the Applications tab. I don't ahve much hope for this working though. :(

---

### Post by Dr_Deadmeat on 2006-06-17
```
andreas@baerbar:~$ glxinfo | grep direct
direct rendering: Yes
andreas@baerbar:~$
```

as you can see I have direct rendering enabled, but still it wont work... I have tried the wiki, but still failure =(

Anyway, what files do you want to see?

---

