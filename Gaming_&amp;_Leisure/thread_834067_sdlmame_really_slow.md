---
title: "sdlmame really slow"
date: 2008-06-19
forum: Gaming &amp; Leisure
---

### Post by ybd on 2008-06-19
Hey, I'm a new Linux user (though not quite a newbie) and installed 8.04 a few days ago. Unfortunately I can't get sdlmame to work - when I set it to use opengl in mame.ini it runs at about 2 fps. Someone suggested to change it to 'soft' and that makes it run at around the 60fps I would want,  however when pressing tab to change options the game slows down to about 40 fps so it's clearly not a good enough solution, as my setup used to run MAME flawlessly under Windows. Not to mention 'soft' looks ugly. Any way to get it to run well?

---

### Post by BigSilly on 2008-06-19
No, you want opengl enabled so you get the proper benefit of Mame.

What's your specs, and are you sure you've enabled your graphics driver? I can't think of anything else it could be. I only have a very basic PC myself, but SDLMame is fantastic on it. You shouldn't be having any bother...

---

### Post by FranMichaels on 2008-06-19
> **BigSilly said:**
> No, you want opengl enabled so you get the proper benefit of Mame.

What's your specs, and are you sure you've enabled your graphics driver? I can't think of anything else it could be. I only have a very basic PC myself, but SDLMame is fantastic on it. You shouldn't be having any bother...

It is slow on my onboard intel card. The best I can do is use Xv to speed it up. I really hope the new version of the intel drivers are much improved, redirected direct rendering works and maybe lxdream would work too.

Getting back to SDLMAME, in your ini, set this for yuvmode (instead of none) Leave the initial "soft" option as is.
```
yuvmode                   yv12x2
```
Now you will get hardware accelerated scaling, which is nice. Yay... :popcorn:

---

### Post by disturbedite on 2008-06-19
on an older onboard chip like an intel, you want opengl disabled to achieve decent performance.

---

### Post by ybd on 2008-06-20
Yeah, fixed it. I just forgot to install the graphics drivers, haha. Works like a charm (and Ubuntu sure is prettier with desktop effects)

---

### Post by BigSilly on 2008-06-20
> **ybd said:**
> Yeah, fixed it. I just forgot to install the graphics drivers, haha. Works like a charm (and Ubuntu sure is prettier with desktop effects)

Oh cool. Glad it wasn't anything any more complex than the drivers. :)

Have fun!

---

### Post by elliottc on 2008-08-14
> **ybd said:**
> Yeah, fixed it. I just forgot to install the graphics drivers, haha. Works like a charm (and Ubuntu sure is prettier with desktop effects)

I have the same situation (including horrible sound).  Can you provide details as to what you installed?

Thanks.

---

### Post by FranMichaels on 2008-08-21
I found a solution for this issue (helps on my intel chipset that's for sure...)

In mame.ini, set antialias to 0

```
antialias                 0
```

Doing that, you can set video to opengl and it works a treat, and no yuvmode needed (now called scaling in sdlmame 127). I recommend disabling the filter option under opengl, if you like your graphics crisp.

As for sound issues, try setting autoframeskip to 1.

:guitar:

---

### Post by eurobeatboy on 2009-03-01
Try enabling the multi-threading option as well.
That increased sdlmame's average speed from 84 to 99 for me.

```
sdlmame -mt
```

---

### Post by jazzakala on 2009-12-06
I was having the same problems that everyone else was having. By downloading the .deb from [http://sdlmame.wallyweek.org/download/](http://sdlmame.wallyweek.org/download/) I was able to resolve this issue. It seems that this is newer than the version of sdlmame available through Synaptic Package Mgr.

---

### Post by kwstas on 2011-03-02
> jazzakala 	 		**Re: sdlmame really slow**
 		I was having the same problems that everyone else was having. By downloading the .deb from [http://sdlmame.wallyweek.org/download/](http://sdlmame.wallyweek.org/download/)  I was able to resolve this issue. It seems that this is newer than the  version of sdlmame available through Synaptic Package Mgr. 	

this solved my problems! i was also helped by the FAQ of that site where was mentioned a problem with alsa sound etc!

---

