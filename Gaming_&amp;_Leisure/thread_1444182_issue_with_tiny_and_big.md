---
title: "issue with tiny and big"
date: 2010-03-31
forum: Gaming &amp; Leisure
---

### Post by nismo_2005 on 2010-03-31
ok so i am trying to install the tiny and big beta. but when i try to install it this is what i get.


> error while loading shared libraries: libCg.so: cannot open shared object file: No such file or directory

but i looked in synaptic for libCg.so and could not find it.

i also tried 

> apt-get install libCg.so

and got

> eading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libCg.so

does anyone have any idea what i need to do? I am still pretty new to linux but i am trying to learn lol.

---

### Post by myromance123 on 2010-04-01
> Please install the Cg toolkit ([http://developer.nvidia.com/object/cg_download.html](http://developer.nvidia.com/object/cg_download.html))

That is from their website. Have you done that first? Its a requirement for the game (works on ATI and NVIDA so dont worry).
I believe what you're missing comes from that toolkit.
Let me know how it goes.

PS: Don't forget to do this as well:
> On Debian/Ubuntu, all you need is to run sudo apt-get install libsdl1.2-all libsdl-mixer1.2 libopenal1
Basically run  this in a terminal before setup:
```
sudo apt-get install libsdl1.2-all libsdl-mixer1.2 libopenal1
```

---

### Post by nismo_2005 on 2010-04-01
i did the 

sudo apt-get install libsdl1.2-all libsdl-mixer1.2 libopenal1
[FONT=monospace]
but i think i forgot to install the cg toolkit. i wil post back and let you know how it go's



-edit-

ok i downloaded the cg toolkit but i cant figure out how to install it. i click the file and it dose nothing and when i type in the path in the terminal it tells me there is nothing there. oh and also when i double click the tinyandbig file nothing at all happens.
[/FONT]

---

### Post by Perfect Storm on 2010-04-01
> **nismo_2005 said:**
> i did the 

sudo apt-get install libsdl1.2-all libsdl-mixer1.2 libopenal1
[FONT=monospace]
but i think i forgot to install the cg toolkit. i wil post back and let you know how it go's



-edit-

ok i downloaded the cg toolkit but i cant figure out how to install it. i click the file and it dose nothing and when i type in the path in the terminal it tells me there is nothing there. oh and also when i double click the tinyandbig file nothing at all happens.
[/FONT]

Just install it via apt-get;
```
sudo apt-get install nvidia-cg-toolkit
```

---

### Post by nismo_2005 on 2010-04-01
ok i am installing now. i will let you guys know the outcome.

---

### Post by nismo_2005 on 2010-04-01
ok apt-get did the trick. but now whenever i go to play the game it comes up i click start and then it go's to the loading screen sets there for like 10-15 sec. and then i here music for a second and then it just closes the game.

---

### Post by Perfect Storm on 2010-04-01
Sounds like a video driver problem. Any output if you run the game via the terminal. Which card do you have?

---

### Post by nismo_2005 on 2010-04-01
i have a bfg nvidia 8400gs 

so far im not liking this card lol. 

this is what i get when i run from terminal 

> /home/eddie/tinyandbig/tinyandbig
This is tiny and big
[init] Log timestamp: Thu Apr  1 13:14:05 2010
[init] Build timestamp: Wed Mar 10 19:47:08 2010
[init] OS: Linux x86
[init] CPU: 
[display] Display requested, but not initialized: using NULL display!
[display] Requested video mode: 1024x576, 32bpp (A8B8G8R8), windowed, no vsync, 16 bit z-buffer, 0 bit stencil buffer
[sdldisplay] Initializing SDL 1.2.13
[opengldisplay] Display mode set: 1024x576, 32bpp (B8G8R8X8), windowed, no vsync, 24 bit z-buffer, 0 bit stencil buffer
[opengldisplay] Vendor: NVIDIA Corporation
[opengldisplay] Renderer: GeForce 8400 GS/PCI/SSE2
[opengldisplay] Version: 3.0.0 NVIDIA 185.18.36
[directoryprovider] Directory 'assets/textures/menu' does not exist!
[directoryprovider] Directory 'assets/sounds' does not exist!
[main] File not found ('tinybigintroloop.ogg') (thrown from loadFromFile (../../../scape/audio/sound.cpp, line 121))


---

### Post by Perfect Storm on 2010-04-01
> [directoryprovider] Directory 'assets/textures/menu' does not exist!
[directoryprovider] Directory 'assets/sounds' does not exist!
[main] File not found ('tinybigintroloop.ogg') (thrown from loadFromFile (../../../scape/audio/sound.cpp, line 121)) 

Seems that something is missing from the game.


If you want a gaming card go for 8800 GT/GTX

---

### Post by nismo_2005 on 2010-04-01
yeah i know that my card is not meant for gaming. i am saving up to build a nice rig for gaming this is my only rig right now though so i try and play a little here and there on it. the rig i have now is going to be a media pc so i figured that the 8400gs would be fine for that.

---

### Post by portets on 2010-04-01
is there a folder titled "assets" in the game's main directory. and in that, a textures and sounds folder?

if so, is there also a "assets.txt" file in the base directory? also, in assets.txt are there these lines as the first few lines?

> assets/sounds/tinybigintroloop.ogg
assets/scripts/menu.lua
assets/textures/menu/menu_04.gif
along with almost 500 other lines.

---

### Post by nismo_2005 on 2010-04-01
all is there except the assets.txt is not

---

### Post by portets on 2010-04-01
here you go:

[ATTACH]152079[/ATTACH]

just put that in the base directory of the game folder

---

### Post by nismo_2005 on 2010-04-01
i put the assets.txt in the base directory and there is still no change. and i still get the same outcome in the terminal.

---

### Post by Yfrwlf on 2010-04-15
I blame a lack of Linux packaging standards, there should be an easy way for programs to request certain versions of certain libraries be installed and whatnot.  Otherwise, they should have packaged those libraries with the game download.

I also blame it on the game being version 0.2 currently, and they are apparently releasing this for PS3, Xbox, Windows, and Mac as well as Linux, so it may also be a matter of priority and because they're trying to make it for so many different platforms.  Of course by the time version 1.0 rolls around no doubt this issue will be resolved.

---

