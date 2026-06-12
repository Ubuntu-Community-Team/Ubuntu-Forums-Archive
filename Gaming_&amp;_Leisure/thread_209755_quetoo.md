---
title: "quetoo"
date: 2006-07-05
forum: Gaming &amp; Leisure
---

### Post by MACRI on 2006-07-05
this is my first post hopefully i put this in the right section.

ok i succesfully installed quetoo the game thats suppose to be like quake. i extracted the .zip and installed through terminal. when i go to load it i get this message:

> ------- sound initialization -------
loading snd_alsa.so sound driver
load /usr/local/lib/quetoo/snd_alsa.so failed: /usr/local/lib/quetoo/snd_alsa.so: cannot open shared object file: No such file or directory

------- video initialization -------
loading vid_glx.so video driver, failed
  /usr/local/lib/quetoo/vid_glx.so: cannot open shared object file: No such file or directory
recursive shutdown
Error: couldn't load vid_glx.so

> they give me these lines to put in terminal in the readme
snd_ref [alsa sdl]; snd_restart
vid_ref [glx softx glsdl softsdl]; vid_restart


and they do crap all. will someone please help me thx, MACRI

---

### Post by MACRI on 2006-07-05
btw im running compiz. if that makes a difference.

---

### Post by SiMoNsAyS on 2006-07-10
can you please upload the compiled bin?
'make install' fails for me:
> In file included from gl_draw.c:22:
gl_local.h:32:21: error: GL/glu.h: No such file or directory
make[2]: *** [vid_glx_la-gl_draw.lo] Error 1
make[2]: se sale del directorio `/home/bio/Desktop/quetoo-0.4.0/src'
make[1]: *** [install-recursive] Error 1
make[1]: se sale del directorio `/home/bio/Desktop/quetoo-0.4.0/src'
make: *** [install-recursive] Error 1

---

### Post by obsrv on 2008-09-21
where can I find x64 debs for quetoo?

---

### Post by obsrv on 2008-09-22
anyone? :S

---

### Post by kingmoffa on 2008-12-12
I've tried to compile quetoo from source on intrepid. No joy. 

Install gcc 4.1 and changing the symlink /usr/bin/gcc and it did compile.

Hope that helps someone finds this useful.

---

