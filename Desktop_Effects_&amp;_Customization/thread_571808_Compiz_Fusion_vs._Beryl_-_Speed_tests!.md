---
title: "Compiz Fusion vs. Beryl - Speed tests!"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by ryanVickers on 2007-10-09
[COLOR=DarkGreen][B][FONT=Fixedsys][SIZE=3]Edit:  I need to make this very clear that I mean _compiz *fusion*_ (the new one), and not the regular old compiz!!!
[/SIZE][/FONT][FONT=Fixedsys][SIZE=3]Edit2:  I know this is not a proper benchmark tool, but it's good enough for here! ;)[/SIZE][/FONT][/B][/COLOR]

I'm not sure if this is the correct place to put this, but oh well.  What I'm wondering is how the average speed of anything in 3D on your computer is affected by beryl or compiz fusion (how much, and if they differ).

My example's are this:
[SIZE=4]    [B][COLOR=Red]_No effects:   _[/COLOR]
[/B]          [I]**glxgears** &#8773; 11,000 to 11,500 fps

[/I]     [B][COLOR=Red]_Beryl:   _[/COLOR]
[/B]          ***glxgears** &#8773; 5,500 to 7,500 fps*[/SIZE]

---

### Post by skymera on 2007-10-09
glxgears ~= 17000FPS

Compiz ~= 8000 FPS

there ya go.

---

### Post by ryanVickers on 2007-10-09
> **skymera said:**
> glxgears ~ 17000FPS

Compiz ~ 8000 FPS

No, no no! it has to be "approximately equal to", not just approximately! ;)

---

### Post by Forlong on 2007-10-09
glxgears is not a proper benchmark tool
You will even get different results when using different GTK themes.

---

### Post by ryanVickers on 2007-10-09
I know it's not perfect, but it's good enough for here - I just want an approximate idea of the impact it has and if they've fixed it for fusion.

---

### Post by overdrank on 2007-10-09
No effects:
glxgears &#8773; 21,318 to 21,420 fps

Beryl:
glxgears &#8773; 14,813 to 15,916 fps

---

### Post by ryanVickers on 2007-10-09
I see 3 people in the poll who have picked that it doesn't slow down at all,I'm wondering about that...

---

### Post by FuturePilot on 2007-10-09
There is a factor that plays in here that some may not know about which could be causing some people to see that there is no difference. If you have SyncToVblank enabled in your Nvidia Settings your FPS will drop to your screen's refresh rate regardless of of whether the effects are enabled or not. If you don't have SyncToVblank enabled then you are going to notice a difference. For example, 
here's what I get with no desktop effects (No SyncToVblank)
glxgears &#8773; 3234.782 FPS
Here's with the desktop effects(No SyncToVblank)
glxgears &#8773;  2990.006 FPS

Now enable SyncToVblank and restart Compiz Fusion
No Compiz (With SyncToVblank)
glxgears &#8773;  60.023 FPS
With Compiz (With SyncToVblank)
glxgears &#8773; 60.023 FPS
60FPS happens to equal my monitor's refresh rate 60Hz
As you can see if someone has SyncToVblank enabled they will not notice a difference.

---

### Post by ryanVickers on 2007-10-09
Your right! 75.5... fps! ;)

---

### Post by xStylezx on 2007-10-10
> **FuturePilot said:**
> There is a factor that plays in here that some may not know about which could be causing some people to see that there is no difference. If you have SyncToVblank enabled in your Nvidia Settings your FPS will drop to your screen's refresh rate regardless of of whether the effects are enabled or not. If you don't have SyncToVblank enabled then you are going to notice a difference. For example, 
here's what I get with no desktop effects (No SyncToVblank)
glxgears &#8773; 3234.782 FPS
Here's with the desktop effects(No SyncToVblank)
glxgears &#8773;  2990.006 FPS

Now enable SyncToVblank and restart Compiz Fusion
No Compiz (With SyncToVblank)
glxgears &#8773;  60.023 FPS
With Compiz (With SyncToVblank)
glxgears &#8773; 60.023 FPS
60FPS happens to equal my monitor's refresh rate 60Hz
As you can see if someone has SyncToVblank enabled they will not notice a difference.

So if im understanding right we should enable SyncToVblank then for a better performance or am i misunderstanding?

---

### Post by FuturePilot on 2007-10-10
> **xStylezx said:**
> So if im understanding right we should enable SyncToVblank then for a better performance or am i misunderstanding?

I'm not sure really. Without SyncToVblank you'll notice high CPU usage with OpenGL stuff. With SyncToVblank you'll notice very low CPU usage with OpenGL stuff. However it comes at a price of FPS. So it depends on which way you want to go. High CPU usage with good performance or low CPU usage with a slight hit on performance.

---

### Post by ryanVickers on 2007-10-10
> **xStylezx said:**
> So if im understanding right we should enable SyncToVblank then for a better performance or am i misunderstanding?


I think you are misunderstanding - yes, there will be no difference between your 60 with or without beryl, but with it off you could get in the thousands (even though there is a difference) ;)

---

### Post by mjwood0 on 2007-10-10
What the sync to blank does it slow down your video so that it's only updating once per screen refresh.  Since OpenGL uses a lot of CPU resources, this is a good option for those not watching movies or playing games as it will reduce your CPU utilization a good bit.

Honestly, I'm wondering exactly what excessively FPS does for a person in normal use.  The screen can only update at lest say 60Hz, so FPS ratings in the 10,000 region or above are really quite excessive -- yet people really worry about them in games...

---

### Post by ryanVickers on 2007-10-10
We see at about 20fps, right (by this I mean that anything over 20fps seems like motion)?  Well, in armagetron, I've noticed that anything under about 60 seems choppy... :p

Talking LCD now (if you weren't already)...
Also, does the refresh rate really make a difference?  Shouldn't the max. update speed be dictated by the fps shown and what your monitor is capable of? (mines 2 ms response (500fps))

---

### Post by mjwood0 on 2007-10-10
This is really a huge can of worms, but here it goes.  

DISCLAIMER: This is my best information -- not fact, just what I have gleaned by research and programming in OpenGL.

To start with, your 2ms monitor (I have one too -- Samsung 22") is really a 5ms panel with a smoothing filter applied.  So it's response is really more of 200fps if we're purely talking about the panel.

That said, your refresh rate is probably around 60Hz.  This is as fast as the graphics card will update the image on your panel or CRT.  Therefore, for normal use, enabling vertical synch is not going to be visible.  

However, game designers decided that this wasn't fast enough and that they wanted to run their games as fast as possible.  Therefore, it's possible to have the back buffer (the video buffer not currently drawn on the screen) updated really really fast.  This is your 300 fps or whatever your game claims.

What happens when you enable VSync in a game is that it throttles the games engine to that speed.  This makes things seem slugish because the game is only running one frame per 16.667ms.  While the output you see may not be any faster, the in-game rendering is much faster without vertical syncing. 

Therefore, setting vsync can really lower CPU utilization making most systems seem faster.  With faster and faster CPUs, this really doesn't matter much.

So that's my understanding.  Hope it makes sense!

Edit for more info:
Enabling vsync is actually a good thing for many reasons.  If your application is processing frames much faster than your refresh rate, or not on an even multiplier, you will get the back buffer half updated when the buffer switch occurs.  This causes the dreaded tearing that many people claim to see.  Therefore, for normal desktop effects, vsync will make things look better (again, theoretically).

---

### Post by ryanVickers on 2007-10-10
Very interesting...
P.S. It's 75Hz ;)

---

### Post by mjwood0 on 2007-10-10
For me, 60Hz on a lcd (without that awful CRT flicker) is just fine.  But yes, 75Hz > 60Hz :)

---

### Post by ryanVickers on 2007-10-10
Now I have proof you were right! ;)  I played armagetron again, and instead of it varying from 500fps to about 50 (rather pathetic - see here), It would stay at around 75 to 71, and whenever it went below that it would seem slower!  I'm going to try it with a lower refresh rate! :twisted: :)

---

### Post by mjwood0 on 2007-10-10
Good to know that all those months working on an OpenGL front end for an embedded system wasn't wasted...  Man did I fight with that &#*($ vertical sync!  

Glad I could be of service :)

You will see some funky artifacts if your FPS drops below your refresh rate as usually, if the back buffer hasn't been filled sufficiently, OpenGL won't switch it out.  This means that your 75Hz refresh rate effectively becomes around 37Hz.  Not too good.

Unless the game is rendering multiple frames per refresh to keep the action or simulation seeming more realistic, getting your frame rate to line up with your refresh will reduce artifacts.

---

### Post by ryanVickers on 2007-10-10
I turned it down to 60, and it ran at 56 fps and was relatively smooth, and this is huge because this normally would have been very choppy! ;)  Except, at this being so low, I noticed slight blurring - it's going back to 75 now, But I may keep the Sync to VBlack on ;)

Now this has me wondering - what does the sync to vblack do when we're talking about "Video Texture adapter" (on), "Video Blitter Adapter" (off) vs. the "OpenGL > Performance" settings?

---

### Post by mjwood0 on 2007-10-10
Honestly?  No idea:confused:

I didn't have those options in an embedded environment...  ergo my knowledge is non-existent!

---

### Post by ryanVickers on 2007-10-10
that's too bad - thanks for the help so fr though!

On a different note (slightly ;)), I tried the effects enabled with the sync to vblack turned on, and I feel sorry for anyone who runs it like that!  It'sw so pathetic!  I would rather just have it off than try and tolerate the effects like *that!* :mad:

I guess I'll leave it off for now, or later, it depends... :p

---

### Post by BryanFRitt on 2007-11-27
To test to see if you can see tearing caused by VSync give yourself 9 or so different desktops and set them each to a different solid color.  Put the mouse over the desktop pager, and spin the mouse wheel.  (Also, you can try this with different pictures, etc...) See if you can notice the difference doing this with VSync on and VSync off. 

p.s. please don't have a seizure while doing this

{0,31,63,95,127,159,191,223,255}

---

### Post by ryanVickers on 2007-11-28
the best test for me is armagetron ;)
I do professional quality benchmark tests with glxgears, armagetron, and firefox XD :lolflag:

---

