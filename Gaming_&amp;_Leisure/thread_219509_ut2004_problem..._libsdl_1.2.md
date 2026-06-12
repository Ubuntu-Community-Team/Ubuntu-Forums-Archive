---
title: "ut2004 problem... libsdl 1.2?"
date: 2006-07-20
forum: Gaming &amp; Leisure
---

### Post by jaywalker on 2006-07-20
ok well im having a problem with ut2004. im running 64 bit kubuntu 6.06. i had ut2004 running fine before i installed all the patches and the ece bonus pack, and now im having a problem. when i try to run it with the launcher i made, it just sits there with the bouncing ut2004 icon and then quits. so i tried running it in the console and i get this:

./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory


can anyone help me with correcting this?

---

### Post by vem0m on 2006-07-20
goto terminal and type:
```
sudo apt-get install libsdl1.2 libsdl1.2-dev
```

then try loading the game then :)

---

### Post by jaywalker on 2006-07-20
did that and it gave me 

Package libsdl1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libsdl1.2debian-nas libsdl1.2debian-arts libsdl1.2debian-oss
  libsdl1.2debian-esd libsdl1.2debian-alsa libsdl1.2debian-all
E: Package libsdl1.2 has no installation candidate


tried to run the game and i get the same:


./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory


and well um... i guess the first thing means it didnt download it correctly right? so, any idea where i could get it if it isnt coming from there?

---

### Post by xeta on 2006-07-20
Try to search for libsdl in synaptic and download the one associated with your sound engine (Alsa, oss, arts, esd, or nas)

package would be: libsdl1.2debian-(soundengine)


Mine was alsa so I installed: libsdl1.2debian-alsa

worked like a charm.

---

### Post by jaywalker on 2006-07-20
> **xeta said:**
> Try to search for libsdl in synaptic and download the one associated with your sound engine (Alsa, oss, arts, esd, or nas)

package would be: libsdl1.2debian-(soundengine)


Mine was alsa so I installed: libsdl1.2debian-alsa

worked like a charm.

well, just so i dont accidentally screw something up more, how do i find out what sound engine im using, or which one i am supposed to download?

---

### Post by DoktorSeven on 2006-07-20
It really doesn't matter much; libsdl1.2debian-alsa should work fine, or -esd if you're using Gnome or -arts for KDE.

---

### Post by jaywalker on 2006-07-20
installed alsa, tried to run, same error.

./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

edit: just tried it with arts instead of alsa since im in kde, and still the same thing.

./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by DoktorSeven on 2006-07-20
**ls /usr/lib/libSDL-1.2***

see if it finds /usr/lib/libSDL-1.2.so.0

If it does, something's screwy.  Seems to be looking in current dir for it in your error, so if it finds that file above, **ln -s /usr/lib/libSDL-1.2.so.0** (use **sudo** before the command if it's outside of your home directory) in the same directory the ut2004-bin executable is in?

---

### Post by jaywalker on 2006-07-20
um ok well i did the command **ls /usr/lib/libSDL-1.2*** and got:

/usr/lib/libSDL-1.2.so.0  /usr/lib/libSDL-1.2.so.0.7.2

so i guess ut2004 is looking for it in its directory and not finding it there.... so should i just copy it over? or how would i rememdy this...?




side question: my ubuntu/kubuntu cds just came in the mail, are they exactly the same as the downloadable versions?

---

### Post by DoktorSeven on 2006-07-20
As I said, try doing a 
**ln -s /usr/lib/libSDL-1.2.so.0**
from the directory that the ut2004-bin file is in.

(If it's outside of your home directory, you need to prefix that command with **sudo **, as in **sudo ln -s /usr/lib/libSDL-1.2.so.0** .)

---

### Post by jaywalker on 2006-07-21
ok so i went to the folder where the ut2004-bin is, ran **ln -s /usr/lib/libSDL-1.2.so.0** in the console and got:

ln: creating symbolic link `./libSDL-1.2.so.0' to `/usr/lib/libSDL-1.2.so.0': File exists

so i go back try to run ut2004, still the same thing

./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

what should i do from here?

---

### Post by vem0m on 2006-07-21
goto terminal and type:
```
sudo apt-get install libsdl1.2debian-all libsdl1.2-dev
```

then try loading the game then :)

should do it this time :)

---

### Post by jaywalker on 2006-07-21
did that, tried loading the game, same old thing:

./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by vem0m on 2006-07-21
for one that is not the proper file to start u goto ur UT2004 directory and type "./ut2004"

try that i think it might do the same thing but that is what file u are suppossed to be starting

---

### Post by jaywalker on 2006-07-21
yea it gives the same error. before i was going there and typing

sh ut2004

but thats what worked before i installed the patches and this error came around...

---

### Post by vem0m on 2006-07-21
ummmm might reinstall then use the mega pack to upgrade and get the extra content they provide that is what i did

---

### Post by chihuahuaman on 2007-09-11
I had the same error message for Bos Wars.  Try installing ia32-libs-sdl
It worked for me.

---

### Post by dmn_clown on 2007-09-11
You shouldn't be starting the game that way. 

In your ut2004 root directory there should be a script aptly named ut2004, ```
sh ut2004
``` will automagically load both the openal and sdl lib that should be in your ut2004/System folder.

---

