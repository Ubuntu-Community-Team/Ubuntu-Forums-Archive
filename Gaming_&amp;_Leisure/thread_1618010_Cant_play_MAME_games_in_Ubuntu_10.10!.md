---
title: "Cant play MAME games in Ubuntu 10.10!"
date: 2010-11-10
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2010-11-10
Hi.

I am unable to play MAME games in Ubuntu 10.10!
In previous Ubuntu releases, setting up MAME was not a problem.
Can someone provide precise steps that must be taken?

Thanks.

---

### Post by DangerOnTheRanger on 2010-11-10
It would be easier if you told us what was wrong.
That way, we could go straight to the problem.

---

### Post by Rytron on 2010-11-10
Okay.

I launch gmameui.
I notice that there are icons missing in it.
Then the message 'No mame executable was found' pops up. I try to add an executable via /usr/games/sdlmame
sdlmame is not there even though it is installed.

---

### Post by Justin_Bailey on 2010-11-11
From a terminal type:

> whereis sdlmame

This should return the location of the binary..

---

### Post by Rytron on 2010-11-11
> **Justin_Bailey said:**
> From a terminal type:



This should return the location of the binary..
```

$ whereis sdlmame 
sdlmame:
```

---

### Post by Justin_Bailey on 2010-11-11
Then you didn't install sdlmame or if you installed it from source something didn't build right.

> sudo apt-get install sdlmame

---

### Post by Rytron on 2010-11-11
> **Justin_Bailey said:**
> Then you didn't install sdlmame or if you installed it from source something didn't build right.

I ran this:

```
$ sudo apt-get install sdlmame
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sdlmame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Strange!

I will install sdlmame from [http://sdlmame.wallyweek.org/download/](http://sdlmame.wallyweek.org/download/)
When I go to install the deb package, I get this warning in Ubuntu Software Center:
[COLOR="Indigo"]Breaks existing package 'mame-common' that conflict: 'sdlmame'. But the '/home/rytron/Desktop/mame_0.140-0ubuntu1~ww1~maverick_i386.deb' provides it via: 'sdlmame[/COLOR]

---

### Post by sifnt on 2010-11-11
I think they recently merged sdl features into the official mame so sdlmame may have been depreciated.

Try launching mame rather than sdlmame. You may need to reinstall mame, and if your frontends depend on sdlmame you probably need to create a symbolic link from /usr/games/sdlmame to /usr/games/mame.

Personally I prefer AdvancedMame as it has some very nice upscaling filters and workers better with my roms. Had to compile it from source but it was worth it, everything is smooth now rather than blocky. See [http://www.google.com/search?client=ubuntu&channel=fs&q=hq4x&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=hq4x&ie=utf-8&oe=utf-8) for examples.

---

### Post by wingnux on 2010-11-11
The binary name changed from "sdlmame" to "mame".

---

### Post by Rytron on 2010-11-11
Yes, [COLOR="Indigo"]/usr/games/mame[/COLOR] did the trick. GMAMEUI now works fine. Thank you all. :popcorn:

---

