---
title: "Nazghul Installation Issues"
date: 2008-02-27
forum: Gaming &amp; Leisure
---

### Post by themattjon on 2008-02-27
Howdy All,

I've been trying to install Nazghul to 7.10 via this link:

[http://gaming.gwos.org/doku.php/guides:64bit:nazghul](http://gaming.gwos.org/doku.php/guides:64bit:nazghul)

Copying anything from 'code' and pasting it to my terminal. Although an icon appears in my Games list, it has no picture and doesn't launch the game.
The folder that was extracted from the download is sitting on my desktop (not really where I want it, but I don't know where to put it).
BTW, my only real experience with Linux thus far is through Gnome, I don't really "do" terminal type stuff yet...

What now?

---

### Post by compiledkernel on 2008-02-28
worked fine for me. 

Open up a terminal type 

nazghul 

hit enter, do you see any output?

---

### Post by themattjon on 2008-02-28
Yeah, command not found.
What if I went back and repeated everything, would that screw stuff up, or just overwrite for better results?

---

### Post by themattjon on 2008-02-29
Ka-Bump!
Maybe I should just stick with NetHack and other native games I can pick with Add/Remove Software?

---

### Post by Perfect Storm on 2008-03-01
Check if you made the launcher correctly. About icon - You need to rename it as it says in the guide:

> Save nazghul.png to your Desktop.


Also did any error showed up while doing the guide (important!).


Next try **haxima.sh**

---

### Post by themattjon on 2008-03-03
Ran into this after copying and pasting the installation info:
> checking for SDL - version >= 1.2.3... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.3 not found!
matthew@matthew-desktop:~/Desktop/nazghul_0_6_0$ make
make: *** No targets specified and no makefile found.  Stop.
matthew@matthew-desktop:~/Desktop/nazghul_0_6_0$ sudo checkinstall

Note: the text refers to 0.6.0 (which I downloaded), while the actual download link is for version 0.5.5 (which I know doesn't work with the guides' terminal info).

---

### Post by Perfect Storm on 2008-03-04
Is your sourcelist correctly set? Check Software sources under system   ---> Administration.

What is the output when running the guides "before installation"

---

