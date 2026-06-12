---
title: "classic compiz trouble"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by drchaos619 on 2007-09-28
I did my fair share of searching before I decided to post this. If my problem was posted in another thread and solved, I apologise ahead of time. 

I'm running Ubuntu fiesty with an ATI 9800 pro card with compiz, emerald and avant.

My compiz has been working wonderfully since I got it all configured and sorted out. However, my video playback was choppy every time I put it into full screen. I already did the X11 video output method, but no dice.

I read about the graphics card driver prog called envy and decided to use it to see if it would solve my problems and voila, it did! however, compiz is shot, emerald is shot and avant is shot. I expected as much but I thought I could figure it out and get it back. 

When I type either emerald --replace or compiz --replace in the terminal, I get the following replies:

emerald --replace

(emerald:6920): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
   
and for compiz:

compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


I know this all started when I upgraded my graphics drivers. I'm still noobish when it comes to linux, so if it's not that much trouble, and replies in plain "duh english" would be appreciated. and again, if this is a repost, I apologise. Instead, direct me to the nearest thread to solve my problem.  

and also on an unrelated note

which one is better? avant or kiba dock? Last I heard, kiba was too unstable, but it looks so damn cool!

---

### Post by drchaos619 on 2007-09-28
I hate to rush things, but this is a bit urgent. again, any help would be great :-D

---

### Post by amadeus266 on 2007-09-29
Have you tried removing and reinstalling CF? I have an ATI 9200 so I didn't have to bother with any strange driver issues or anything like that. On the second issue- I have Kiba-dock from trevino's repo and it works beautifully.

Try this: [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

### Post by drchaos619 on 2007-09-29
Yeah I've tried reinstalling it and so on. Obviously, I got nada. In the sessions menue on the logon screen, XGL with GNOME wasn't an option so I did a little terminal magic that I got from a tutorial in effort to make it an option. Whenever I select it as an option and log it, It goes nuts and the on screen graphics are well, maybe half rendered and honestly looks like snow from a tv screen with no feed comming to it. 

No dice thus far. any others for some advice?

---

### Post by drchaos619 on 2007-09-29
delete this thread, mods. I asked the same question in an ongoing thread

---

