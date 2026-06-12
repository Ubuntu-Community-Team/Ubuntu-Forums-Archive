---
title: "trying to install SDL1.2 or greater"
date: 2006-07-08
forum: Desktop Environments
---

### Post by platinum on 2006-07-08
hi. i'm trying to install SDL1.2 or greater, and i can't seem to find it in the synaptic package manager.

can someone post the apt-get command line for SDL ?

---

### Post by platinum on 2006-07-08
no worries, found what i needed ! :D 

 apt-get install libsdl1.2debian-all

just couldn't remember the package name!

---

### Post by platinum on 2006-07-08
damn. still not working. when i go to install zsnes, it says this at the bottom:
"
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: SDL >= 1.2.0 is required
"

??what does it mean? i just installed SDL!!!

---

### Post by Fluffy, the jolly sheep on 2006-07-08
When you compile zsnes yourself like you seem to be trying, you'll need the development package of sdl (libsdl1.2-dev) and of any other package it depends upon. 
But you're probably better of installing the binary compiled version of zsnes in the repositories using synaptic or add/remove software (use the search function to find it). It will save you lots of compiling trouble.

---

