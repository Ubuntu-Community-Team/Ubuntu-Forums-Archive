---
title: "NWN - no sound in movies problem"
date: 2007-08-31
forum: Gaming &amp; Leisure
---

### Post by cogadh on 2007-08-31
Okay, I've followed several how-tos and I can get Neverwinter Nights installed about seven different ways now, but I have only found [one how-to that describes installing the movie files]("http://ubuntuforums.org/showthread.php?t=113259"). Unfortunately, after following that how-to, the movies work, but they don't have any sound. One of the readmes that comes with that how-to describes compiling a custom libSDL to fix the problem, but following it produces nothing. I can't find any newly created library files after running make. I can only assume that there is a step missing somewhere, but I don't know what it might be. Here are the instructions as they appear in the readme:
```
1) Download the SDL source. (Say 1.2.7, in this example)
2) gzip -d -c SDL-1.2.7.tar.gz | tar xvof -
3) cd SDL-1.2.7
4) vi src/video/SDL_video.c
5) Remove the word 'static' from in front of the SDL_WM_GrabInputRaw() 
   declaration.

	Line 1760, for SDL 1.2.7
	ex:

static SDL_GrabMode SDL_WM_GrabInputRaw(SDL_GrabMode mode)

to

SDL_GrabMode SDL_WM_GrabInputRaw(SDL_GrabMode mode)

6) ./configure --enable-alsa
	- Not certain what other options you might need. 
	- Configure should figure it all out. 
	- --prefix is irrelevant, as you won't be installing this copy of
	  libSDL in any system wide directory. 

7) make

8) cp ~nwn/lib/libSDL-1.2.so.0 ~nwn/lib/libSDL-1.2.so.0.bioware
	- Backup the Bioware supplied libSDL, if you've not backed it up
	- from the earlier steps. 

9) cp src/.libs/libSDL-1.2.so.0.7.0 ~nwn/lib/libSDL-1.2.so.0
```
Right off the bat, I am trying this with SDL 1.2.12 sources, not the 1.2.7 sources listed in the readme. At step 8 is where I discovered the problem, there is no "src/.lib" directory. In fact there are no hidden directories at all.

I don't normally ever compile from source (had too many bad experiences like this with it), but this is one case where I am willing to take a chance. If anyone has any ideas on what I have missed, I'd appreciate it.

EDIT - Probably also should have mentioned, if someone knows about an actual confirmed working solution to the no sound problem that doesn't require a newly compiled libSDL, I will gladly take that info instead of help with the compile. I just want the sound in the movies to work, it doesn't really matter to me how I do it.

---

### Post by cogadh on 2007-09-01
So no ideas, huh?

---

### Post by cogadh on 2007-09-03
Okay, this is odd, but sound suddenly started working in the movies, though with a little bit of static. The only changes I had made were to remove all of the things I had previously tried to get the sound working (deleted a custom .asoundrc, removed "aoss" from the Bink Player launch parameters, etc.), none of which should have made the sound work. 

After a little more experimenting, I discovered that sound in the movies only works if I have my [last.fm player](http://www.last.fm) running, but not actually playing any music. I don't know why that would work, but I'm not complaining, NWN now runs completely natively, movies and all. Just finished copying my saves from my Windows install and now I'm off to play!

---

