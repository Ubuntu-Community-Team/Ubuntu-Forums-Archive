---
title: "3d rendering on ubuntu"
date: 2009-05-10
forum: General Help
---

### Post by mayankbhagya on 2009-05-10
i am a noob at ubuntu (& linux as well)..

i wish to try hands at 3d rendering in opengl integrating it with C.
i have a nvidia geforce 8400m gs and want to utilize it the most.

plz suggest a library for C which i can get from the repositories and compile opengl programs.

i heard about mesa, glut, gtk, sdl and many more names...
plz suggest the best and nvidia compatible library.

thanx

---

### Post by abhilashm86 on 2009-05-10
well you can use freeglut to compile OpenGl programs, before that you need to have graphics driver, so enable your graphics card, 

go to software sources, enable backports,
then,You have to install the development packages of the glut libraries
```

sudo apt-get install freeglut3-dev libglut3-dev

```


and then link against the libraries using g++ compiler,
```

-lm -lGL -L/usr/X11R6/lib -lGLU -lglut

```

i'm doing opengl using this way :)

---

### Post by abhilashm86 on 2009-05-10
> **mayankbhagya said:**
> i am a noob at ubuntu (& linux as well)..

i heard about mesa, glut, gtk, sdl and many more names...
plz suggest the best and nvidia compatible library.

thanx

glut performs almost all functions in opengl, as we are creating GUI, so you can look around opengl.org, is your graphics card enabled??
is not enabled, opengl will execute a bad window...........
you can also link with cc or gcc compiler, 

```
-lm -lGL -L/usr/X11R6/lib -lGLU -lglut

```

---

### Post by abhilashm86 on 2009-05-10
also get the basic compilers and headers here,
```

sudo apt-get install build-essential

```
then compile............

---

### Post by mayankbhagya on 2009-05-10
Thankz 'abhilashm86' for the help..
i installed nvidias recommended latest driver.
i think that enables my graphic card.

but i dint quite get the backport thing.

and regarding glut.., are you sure they do not have any conflicts with nvidia cards..? i think there are some issues.

N i have gcc; i think libraries r fine with them if nvidia has no issues.

Regards

---

### Post by abhilashm86 on 2009-05-10
> **mayankbhagya said:**
> Thankz 'abhilashm86' for the help..
but i dint quite get the backport thing.

and regarding glut.., are you sure they do not have any conflicts with nvidia cards..? i think there are some issues.

N i have gcc; i think libraries r fine with them if nvidia has no issues.

Regards
backport enable means you can install some propritery software on ubuntu like nvidia drivers ans others, to enable, go to

system->administration->software sources -> updates tab ,there you have backports...............

initially to install NVIDIA graphics drivers, ubuntu will detect hardware graphics card and install it,

can you check system->administration->hardware drivers, and tell whats installed there??

---

### Post by mayankbhagya on 2009-05-11
Thanx again..
i enabled backports..
and also, after i installed the nvidia driver, it shows the same in:
 system -> administration -> hardware drivers

i.e. the latest driver.. nvidia 180.51

i also downloaded libgl-dev i.e. the mesa.. it is working fine..

i tested a sample program too.

that library is fine, isn't it..?

---

### Post by abhilashm86 on 2009-05-12
> **mayankbhagya said:**
> Thanx again..
i enabled backports..
and also, after i installed the nvidia driver, it shows the same in:
 system -> administration -> hardware drivers

i.e. the latest driver.. nvidia 180.51

i also downloaded libgl-dev i.e. the mesa.. it is working fine..

i tested a sample program too.

that library is fine, isn't it..?

yes there is no problem with library at all :) most importrant part of graphics opengl or maya or anything is graphics card and frame buffer, so you have right key, move on, NVIDIA is really great and easy to install drivers through backport, but intel and others you need to play a lot to install...............

---

