---
title: "Slune won't start"
date: 2007-04-26
forum: Gaming &amp; Leisure
---

### Post by j.miller565 on 2007-04-26
I'm trying to get Slune to work, but when I try it in the Terminal this error comes up:
```

simon@simon-desktop:~$ slune
* Slune * Slune lives in /usr/share/games
* Soya * Using 8 bits stencil buffer

* Soya * version 0.12
* Using OpenGL 2.1.0 NVIDIA 96.31
*   - renderer : GeForce FX 5200/AGP/SSE/3DNOW!
*   - vendor   : NVIDIA Corporation
*   - maximum number of lights        : 8
*   - maximum number of clip planes   : 6
*   - maximum number of texture units : 4
*   - maximum texture size            : 4096 pixels
* Using OpenAL 1.1
*   - renderer  : Software
*   - vendor    : OpenAL Community

* Slune * (Psyco not found ; if you are using an x86 processor, installing psyco can speed up Slune a little)
Exception exceptions.OverflowError: 'long int too large to convert to int' in '_soya._Material._pack' ignored
Segmentation fault (core dumped)

```

Is there anything I can do to solve this problem?

---

### Post by cogadh on 2007-04-26
I get the same exception error, but not the Psyco warning (I have Psyco installed). It looks like a problem with the Python code. Either the interpreter or the JIT compiler is having issues with it (I think, I'm not really a programmer). I couldn't find any info on the Slune site about this error (or any errors, there's not a lot there) and Google search turned up a lot of nothing. Sorry friend. :(

EDIT - How's this for coincidence: I just installed Balazar, a different game that runs on the same Soya3D engine. It actually launches to a startup screen, but once you try to start the game, the same overflow error occurs in the same "soya._Material._pack". I'm going to file a bug report and see if that gets any answers.

---

### Post by j.miller565 on 2007-04-26
ok that's cool. thanks cogadh

---

### Post by JuliusCes on 2007-04-29
I have the same problem as well.

With Ubuntu 6.10, I didn't have any problems running Slune, but now that I updated to 7.04, I got the same error message

---

### Post by cogadh on 2007-04-30
Here's a link to the bug report I filed (no action on it yet):
[https://gna.org/bugs/?9008](https://gna.org/bugs/?9008)

---

### Post by szantaii on 2007-04-30
I have the same problem on 7.04, but on 6.10 there was no such error.
```
$ slune
* Slune * Slune lives in /usr/share/games
* Soya * Using 8 bits stencil buffer

* Soya * version 0.12
* Using OpenGL 1.3 Mesa 6.5.2
*   - renderer : Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
*   - vendor   : Tungsten Graphics, Inc
*   - maximum number of lights        : 8
*   - maximum number of clip planes   : 6
*   - maximum number of texture units : 8
*   - maximum texture size            : 2048 pixels
* Using OpenAL 1.1
*   - renderer  : Software
*   - vendor    : OpenAL Community

* Slune * (Psyco not found ; if you are using an x86 processor, installing psyco can speed up Slune a little)
Exception exceptions.OverflowError: 'long int too large to convert to int' in '_soya._Material._pack' ignored
Segmentation fault (core dumped)
```

---

### Post by xmido on 2007-05-14
yes same also, black screen opens for a sec then the game closes :confused:

---

### Post by cogadh on 2007-05-22
This bug was fixed with the latest version of Soya 3D (0.13.1). Apparently there was a problem with Soya and Python 2.5 that has now been corrected.

---

### Post by szantaii on 2007-05-24
That is good news, but now will there be an update to slune or something?

---

### Post by cogadh on 2007-05-24
I haven't seen anything about an update for Slune (yet), and there currently isn't a .deb for Soya 3D 0.13.1 (I could only find 0.12.1), so until the update gets packaged, I think the only way to get it is to compile from source. That's not always the easiest thing to do, so I don't necessarily recommend it.

If you want to try, the Soya 3D source can be found here: [http://download.gna.org/soya/](http://download.gna.org/soya/)
You'll want the file Soya-0.13.1.tar.bz2. As for compile instructions, someone smarter than I will have to provide them.

---

### Post by szantaii on 2007-05-25
Thanks, I'll try to compile it from source if I'll have a little time.

---

### Post by header2k on 2007-06-27
I haven't compiled it.
I installed python2.4 and edited the first line in /usr/games/slune from:
```
#!/usr/bin/python -O
```
to :
```
#!/usr/bin/python2.4 -O
```
and it works!

ps: Sorry for my bad English.

---

### Post by cogadh on 2007-06-27
Ha! Sometimes the solution is just too simple to see clearly. Nice work header2k. :)

EDIT - Just an FYI, this also fixes the problem I had with Balazar.

---

