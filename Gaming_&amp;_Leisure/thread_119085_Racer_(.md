---
title: "Racer :("
date: 2006-01-18
forum: Gaming &amp; Leisure
---

### Post by curuxz on 2006-01-18
I cant get racer to run, i keep getting :

./racer: error while loading shared libraries: libfmod-3.61.so: cannot open shared object file: No such file or directory

But cant find this lib in the repo's or online anywhere. The few places that say they have it never work :(

Help getting this game working would be great, it looks soooo cool.

---

### Post by Perfect Storm on 2006-01-18
here's the file. Now copy it in the right directory.

---

### Post by curuxz on 2006-01-18
Thanks AI! :D

---

### Post by curuxz on 2006-01-18
Dammit, now it says this:
```

** Warning: QInfo: can't open 'gfx.ini'
  local host: 'curuxz'/10.0.0.252
** Warning: QInfo: can't open './racer.ini'
** Warning: QInfo: can't open './gfx.ini'
** Warning: QInfo: can't open './debug.ini'
RTime:Reset()
** Warning: QImage ctor: can't load 'data/images/skidmark.bmp'
** Warning: QImage ctor: can't load 'data/images/smoke.tga'
** Warning: QImage ctor: can't load 'data/images/repbuts.tga'
RAudio ctor
RAudio:Load(); enable=0
FMOD initializing
** Error: FMod; old library! You should be using at least v3.61 (see www.fmod.org)
Disabling FSOUND output (NOSOUND)
** Error: Can't init FMOD: An invalid parameter was passed to this function

```
and then goes back to the promt :(

---

### Post by charlieg on 2006-01-19
Play [VDrift](http://www.vdrift.net) instead.  It's FREE rather than freeware, so has better future prospects IMHO.

---

### Post by curuxz on 2006-01-19
Racer is FAR more advanced looking at the screenshots I wana give all the free linux games a go, and vdrift is on my list ;)

---

### Post by Biased turkey on 2006-01-19
[QUOTE=charlieg]Play [VDrift](http://www.vdrift.net) instead.  It's FREE rather than freeware, so has better future prospects IMHO.[/QUOTE]

Thanks a bunch for the link Charlieg, imho what Linux always missed so far was a good racing game. Forget "Racer", it has  great cars and tracks but no AI to race against and it's not open source.
I prefer "real racing sims " like GP Legends or Richard Burns Rally over drifting so I hope someone will come with a "real racing sim" fork to vdrift.
For sure, installing Vdrift is on my todo list for the next week end.

---

### Post by curuxz on 2006-01-19
why is it not open source??? they provide the source code on the site.

---

### Post by Biased turkey on 2006-01-19
[QUOTE=curuxz]why is it not open source??? they provide the source code on the site.[/QUOTE]

Oops, apology for posting some misinformation. Racer source code is indeed downloadable.

---

### Post by curuxz on 2006-01-19
Still no solution to my problem tho :( Vdrift seems a bit under developed at the moment, has potential but im not very good at this drift-stearing lark :(

---

### Post by kumpf on 2006-01-19
I saw a new version of FMOD was posted, but the game may only be looking for a specific version.. try the one I've attached.  it's directly from an older version of racer.

also, if you can't build it yourself, try the LOKI install.
([http://www.liflg.org/?catid=6&gameid=13]("http://www.liflg.org/?catid=6&gameid=13"))

Racer is such an awesome simulator.. I've run it on a windoze box and it rocks out.. we need to get this up and rolling the in the Ubuntu repositories! :)

I think the creators are quite excited about linux distros, but mainly release as .EXE since the majority of people that use it right now run windows.. but they are nice and continue to release the source.  and if it's easy to install (yay repositories!), a lot of Linux people could like it toooo!

---

### Post by curuxz on 2006-01-19
many thanks dude, trying your suggestions now :D

this is why i love ubuntu so much, its debian but with better people!

EDIT: LOKI install worked a dream, i had herd of it but could not find it. thanks so much!

---

### Post by kumpf on 2006-01-19
Awesome! great to hear you got it working! 

How hard do you think it is to get this program in a repository.. I think I'll go post a note in one of the repository suggestion threads..  :)

happy gaming! :)  I may just go make a steering wheel and some pedals with a couple potentiometers I have around here.  a weekend project perhaps! :KS

---

### Post by curuxz on 2006-01-19
I cant seem to find a way to change the controls, or for that matter any of the settings, any ideas?

I defo want games like this added to the repos (as you will probs see from another thread i started a few days ago about racer and Vdrift)

---

### Post by kumpf on 2006-01-19
The game is pretty well layed out.. I think that there is a menu on the front page of the game called "Options".  There should be a controls section within that. If you can't seem to do what you want there, poke around in the .ini files.  Most of them are very "human readable" and can be figured out with a little patience.

Good luck and happy racing! :)

---

### Post by charlieg on 2006-01-20
[QUOTE=curuxz]why is it not open source??? they provide the source code on the site.[/QUOTE]
They provide the source code for an older version and the source code is not available under a free software compatable license.  i.e. you can compile Racer for yourself, and that's about all you are allowed to do.  It is not a Free game, just freeware.  You will not get a source code download for more recent releases.

From the site:
[QUOTE=www.racer.nl]**08-07-03**: The v0.5.0 source code has been released. This is for Linux actually, though you can make it work on Mac/Windows as well. This is the last source version I will release for Racer (but the executables will still be free as normal). See the download page.[/quote]
You can call that open source if you like, even if it was 2.5 years ago.

---

