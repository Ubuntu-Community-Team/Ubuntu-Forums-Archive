---
title: "I don't know how to use mednafen!"
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by Bumblescrump on 2006-08-10
Hey I just installed metnafen, it went great, but now, I don't know how to start it!! someone please help!:confused:

---

### Post by DoktorSeven on 2006-08-10
Go to a command shell and type

**mednafen /path/to/rom** (wherever the ROM you wish to run is)
 
Once in, hit **F3** to configure controls.

**mednafen --help** should give you some commandline switches to help you out.

---

### Post by bugz0r on 2006-09-15
it says:

bash: mednafen: command not found

I know this is an old thread but I thought its better than starting another one.

---

### Post by DoktorSeven on 2006-09-15
How did you install mednafen?

---

### Post by bugz0r on 2006-09-15
i CD'd into the mednafen folder which is in my home folder. then I did ./configure followed by make.

---

### Post by DoktorSeven on 2006-09-16
You need to follow that up with 
**sudo make install** or **sudo checkinstall** (checkinstall builds a debian package and installs it, make install just installs manually).

---

### Post by bugz0r on 2006-09-16
Mednafen is working... i guess but the ROM will not open.

bash: //home/USERNAME/FE.gba: Permission denied

---

### Post by DoktorSeven on 2006-09-17
You have to run mednafen with the GBA ROM as an argument, as so:

**mednafen /home/USERNAME/FE.gba**

If you're doing that, make sure FE.gba has read permissions:

sudo chmod 644 /home/USERNAME/FE.gba

---

### Post by XVampireX on 2006-09-17
Weird, I didn't have to change any permissions, unless his/her system is a multi user system, that really shouldn't be the case.

Also, it's not neccessary to point out the full path to the file, just cd to the directory where the file/s are and do:

```

mednafen rom.gba

```

P.S: I have played around with the settings and it looks like OpenGL is not the best choice for mednafen, using SDL in vdriver (set it to 1 instead of 0) would allow for some mostly the same gameplay speed/quality but what I saw is that OpenGL doesn't allow fast forward as it is supposed to be, so it is useful most of the time to use SDL instead of OpenGL.

---

### Post by bugz0r on 2006-09-17
Thanks for all the help DoktorSeven, everything is working fine.

---

