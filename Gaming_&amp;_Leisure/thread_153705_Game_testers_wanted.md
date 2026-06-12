---
title: "Game testers wanted"
date: 2006-04-01
forum: Gaming &amp; Leisure
---

### Post by Jacky_J on 2006-04-01
Hey guys,
So for our senior project our group is making a game. I'd like to get some people to try it out and see what they think, find bugs, etc.

[http://emptyclip.sourceforge.net/](http://emptyclip.sourceforge.net/)

The game is like diablo, with the controls set up like crimsonland/alien swarm.  The game right now is extremely imbalanced, but the single player component is mostly done.

-Linux version-
I won't be able to release the source code until the semester is over, so you'll have to settle for the precompiled binaries.

The game uses the following libraries:
SDL
SDL_image
SDL_net
freetype
fmodex

You also need 3d hardware acceleration working. i.e the command

```
glxinfo | grep rendering
```

needs to say yes

fmod can be found here:
[http://www.fmod.org/ifmoddownload.html](http://www.fmod.org/ifmoddownload.html)

Installation of fmod is pretty easy, except for you have to make sure /usr/local/lib is in your library path.

so basically add the line
/usr/local/lib

to /etc/ld.so.conf, then run
```
sudo ldconfig
```

I've tried it with Ubuntu 5.10 and 6.06.  However, i did have one problem with dapper where ubuntu would freeze after fmod gets shutdown.  So i'm not sure whether it's a bug in dapper or fmod, or a combination of the hardware.  

Anyway, if you have any questions you can post back here or email me.  Your feedback would be greatly appreciated.

Thanks

---

### Post by charlieg on 2006-05-29
Looks like testing was good - I see you're on happypenguin.org now!

Ironically, looking for fmod installation instructions brought me to this post.

---

### Post by charlieg on 2006-05-29
Perhaps you could investigate a distro-neutral installation method to overcome problems such as fmod not being installed?

e.g.:
[www.autopackage.org](www.autopackage.org)

---

### Post by Jacky_J on 2006-05-30
[QUOTE=charlieg]Perhaps you could investigate a distro-neutral installation method to overcome problems such as fmod not being installed?

e.g.:
[www.autopackage.org](www.autopackage.org)[/QUOTE]

I'll give it a look.  I was thinking about including the fmodex libs but then i decided to leave them out for certain reasons.  I may come back to the idea though.

BTW, i liked your blog site.  The game is called "Empty Clip" (singular), in which the misspelling lead to a broken link.

---

### Post by Perfect Storm on 2006-05-30
Wouldn't it give lisence issue if you include Fmod?

---

### Post by Jacky_J on 2006-05-30
[QUOTE=Artificial Intelligence]Wouldn't it give lisence issue if you include Fmod?[/QUOTE]
I emailed them about that and they said since it was an open source project, it wouldn't matter because it doesn't affect them.

---

### Post by XVampireX on 2006-05-31
Which fmod package am I supposed to get? There are quite a few (Not to mention there's also fmod ex).

Thanks.

---

### Post by Jacky_J on 2006-05-31
[QUOTE=XVampireX]Which fmod package am I supposed to get? There are quite a few (Not to mention there's also fmod ex).

Thanks.[/QUOTE]
You can just get the general linux version:

[http://www.fmod.org/files/fmodapi40404linux.tar.gz](http://www.fmod.org/files/fmodapi40404linux.tar.gz)

---

### Post by charlieg on 2006-05-31
Out of curiousity, why use fmod over other sound libraries such as SDL_mixer?

---

### Post by Jacky_J on 2006-05-31
[QUOTE=charlieg]Out of curiousity, why use fmod over other sound libraries such as SDL_mixer?[/QUOTE]
We initially started out with SDL_mixer, but had some problems with it freezing / dropping out.   We used code from various SDL_mixer tutorials, but we could never figure out the problem.  The guy in our team that did the sound found fmod, and said that it was a million times better.  So far we haven't had any problems with it.  It's a pretty solid sound engine.

---

### Post by Zyphrexi on 2006-06-03
> Ironically, looking for fmod installation instructions brought me to this post.

heh I came here for the same reason, I loved crimsonland but was severely beefed that it wouldn't run under wine, a game like empty clip is sorely needed.

---

### Post by GordonBeMe on 2007-12-16
this work on linux o/s only or will it woprk on windows o/s?

---

### Post by matthewcraig on 2007-12-16
How is the beta test going?  Last update was 18 months ago...

---

### Post by darkazurka on 2009-04-08
> **Artificial Intelligence said:**
> Wouldn't it give licence issue if you include Fmod?
(I misquoted you by fixing the typo of lisense to license)

This free software(emptyclip) depends on non-free software(fmodex). fmodex has restrictions regarding commercial use.

---

