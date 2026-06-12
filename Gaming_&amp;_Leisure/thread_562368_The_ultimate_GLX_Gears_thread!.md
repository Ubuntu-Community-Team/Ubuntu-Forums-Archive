---
title: "The ultimate GLX Gears thread!"
date: 2007-09-28
forum: Gaming &amp; Leisure
---

### Post by Sockerdrickan on 2007-09-28
What FPS do you get? :D

run this: glxgears

I get 20783 FPS :popcorn:

---

### Post by hikaricore on 2007-09-28
I **was** getting about 14,000 but after switching to an SMP kernel I'm getting about 5,000.

Not sure why, the performance is much better and my video hardware is now working much more smoothly.

---

### Post by Baby Boy on 2007-09-28
2446.807 FPS 

Not much to brag about I guess ;).

---

### Post by jpyanowski on 2007-09-28
I get 1400 but then I'm downloading some games so that may have an effect on the system.

---

### Post by cogadh on 2007-09-28
6281.556 FPS

But, since the human eye cannot detect the difference over and above 40 to 60 FPS, I'm pretty happy with that.

---

### Post by Gordy on 2007-09-28
> **Tux0r said:**
> What FPS do you get? :D

run this: glxgears

I get 19 253 FPS :popcorn:



Is this good or bad?

34237 frames in 5.0 seconds = 6847.256 FPS

---

### Post by Sockerdrickan on 2007-09-28
> **cogadh said:**
> 6281.556 FPS

But, since the human eye cannot detect the difference over and above 40 to 60 FPS, I'm pretty happy with that.

?:S You can detect a lot more than you think, 40fps is not good on your eyes dude :(


> **Gordy said:**
> Is this good or bad?

34237 frames in 5.0 seconds = 6847.256 FPS

Yes that is good

---

### Post by cogadh on 2007-09-28
> **Tux0r said:**
> ?:S You can detect a lot more than you think, 40fps is not good on your eyes dude :(
Are you sure you are not thinking of refresh rate? A refresh rate of 40Hz would be bad for your eyes, but the frames per second of an application just indicates how smooth the animation will be. Most people can't see the framerate difference once you get into the 50 frames per second range and nobody can tell the difference once you get above 60 fps, the human eye just isn't capable of that. It's kind of like 24 bit color vs 32 bit color, the human eye cannot actually interpret the differences between all of the millions of possible colors, so both will look the same.

---

### Post by Cappy on 2007-09-28
The eye can actually tell upto 70 FPS for a flicker free image. It depends on a lot of factors and it can be upto twice that. (google if you want to know more)
For games 40 FPS is usually good enough.

The real reason for a high FPS is so that when you reach a section of a game that requires tons of rendering that the FPS won't dip below 40.

So basically I'm saying that it matters more that your FPS stays above 40 than whatever FPS you might get the majority of the time.

By the way, glxgears isn't a benchmark. See:
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

### Post by rybu on 2007-09-28
These numbers that GLXgears outputs, what do they mean exactly?  On my laptop it gives me a tad just over 10,000fps.  But that's not frames per second as my screen isn't capable of that kind of performance (I don't know of any computer screen that is).  So what is being counted exactly?

---

### Post by beeldings on 2007-09-28
```
91628 frames in 5.0 seconds = 18325.475 FPS
```

Not too bad for an old socket 754 system. :)

---

### Post by cogadh on 2007-09-28
> **Cappy said:**
> The eye can actually tell upto 70 FPS for a flicker free image. It depends on a lot of factors and it can be upto twice that. (google if you want to know more)
For games 40 FPS is usually good enough.
I did Google it and *on average* anything above 60 FPS in video games is just gravy. It really depends on your monitor, the lighting conditions and how good your vision is. If you have perfect 20/20 vision, have a large, high definition monitor and are playing in perfect lighting conditions, then yes, you *might* see a difference between 60 FPS and 100 FPS. However, most of us probably don't meet all those requirements and won't see any difference.

Oh, and I want to amend my previous glxgears result. Apparently, not only is it not a good benchmark, it is also not consistent. I'm now getting 16192.506 FPS, almost 10000 FPS faster than before (and I didn't make any changes to my system at all).

---

### Post by Sockerdrickan on 2007-09-29
40 fps is lag for me on a 60hz screen, that's all I can say :)

---

### Post by leech on 2007-09-29
> **cogadh said:**
> Are you sure you are not thinking of refresh rate? A refresh rate of 40Hz would be bad for your eyes, but the frames per second of an application just indicates how smooth the animation will be. Most people can't see the framerate difference once you get into the 50 frames per second range and nobody can tell the difference once you get above 60 fps, the human eye just isn't capable of that. It's kind of like 24 bit color vs 32 bit color, the human eye cannot actually interpret the differences between all of the millions of possible colors, so both will look the same.

That's correct about the refresh rates, though with color depth the difference between 24bit and 32bit are not noticeable because the extra 8bit is for the alpha channel to handle transparencies and the like.

The break down of color is 8bits red, 8bits green, 8bits blue and 8bits of alpha.  Each set of 8 bits allows a total of 256 shades of that color, so you times the 256*256*256 of RGB and you get the 16.7million colors.  On the other hand you have the Matrox Parhelia video card that actually supported 30bit color (not sure about the alpha channel there, I guess if it was matched with 10bit alpha channel, it would really be 40bit color) that actually supported billions of colors.

The Sync to Vertical Refresh that you see in many game option screens will limit your frames per second according to what the refresh rate of your game is.

The only thing I've ever noticed when a game runs at faster than 100fps is that if looks almost like watching a river flow.  It's very fluid.  For example, play Quake2 on a modern computer system and you'll see what I mean.

Sadly my computers are getting old, so I'm lucky on newer games to get an average of 30fps.

On my laptop, glxgears gets about 3700 with compiz not running.  Then again, it's 'only' a 2ghz Centrino with a nvidia 6600 Go (that is underclocked from what I've read on the net).

Leech

---

### Post by Sisophon2001 on 2007-09-29
> **rybu said:**
> These numbers that GLXgears outputs, what do they mean exactly?  On my laptop it gives me a tad just over 10,000fps.  But that's not frames per second as my screen isn't capable of that kind of performance (I don't know of any computer screen that is).  So what is being counted exactly?

I did not look at the code, but my understanding is that it is recording the speed the program runs internally. The program updates the animation each run through its drawing loop. In your case is looping through its drawing loop 10,000 times per second.

If it waited for a screen sync, the it would run at your monitor refresh rate always. This is not a good idea for games because the game speed would depend on your refresh rate.

Normally games need to have timers so they vary the movement between each frame so as to give a constant speed no matter which system they are run on. A car racing game must be playable on every system. The extra time can be used for more complex calculations, like a more detailed rendering of the background. A high FPS count in GLXgears will translate into higher definition rendering in a good quality game, rather than any speed increase which would be unwanted. Most games will look for a balance of between 40 to 60 FPS, with the maximum detailing.

Below 30 FPS the game will look bad, but I agree you can notice the difference between 30 and 60, and possibly higher. 30 FPS is the practical cut-off limit below which a game is unplayable.

Garvan

---

### Post by cogadh on 2007-09-29
> **Tux0r said:**
> 40 fps is lag for me on a **60hz screen**, that's all I can say :)
There's your problem, I would get a headache no matter what FPS a game was running at if my monitor was working at 60Hz. I don't keep it any lower than 75Hz (usually set for 85Hz).

---

### Post by Sockerdrickan on 2007-09-29
Actually mine is 60 or 75, I never know because games won't let me pick Hz lol

---

### Post by Sockerdrickan on 2007-11-22
OMG! guys install the new nVidia driver!

I get 20783 fps
I used to get 19500 fps

---

### Post by mthakur2006 on 2007-11-22
i get 538 fps :(

---

### Post by Sockerdrickan on 2007-11-22
I am sorry :(

---

