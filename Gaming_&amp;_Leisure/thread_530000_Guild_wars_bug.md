---
title: "Guild wars bug"
date: 2007-08-19
forum: Gaming &amp; Leisure
---

### Post by Tyke91 on 2007-08-19
I got guildwars today (yay :D ) and i got it working twice... 

but now whenever i try to run it, it loads it's little connection screen, and before it gets to the login page it becomes a wierd desktop eating monster and freezes like that

i got a screenshot

[http://server5.pictiger.com/img/1272606/picture-hosting/-home-mykola-desktop-screenshot.png](http://server5.pictiger.com/img/1272606/picture-hosting/-home-mykola-desktop-screenshot.png)

what's going on?

(my desktop is not black and it takes around 5 minutes for the effect to go away... also, my resolution is stuck like that (mine is much higher) )

---

### Post by MWilliams13 on 2007-08-20
I have been trying to get Guild Wars to work on my PC so how did you do that?

And your answer (or so I think):I think that Wine is not being able to keep up with gameplay. It does the same with Age of Mythology. It can play for awhile then cuts off. I would say your best bet is to Google, "Guild wars in Wine guide" then click a few links and try and find an answer. Or if that dosen't help ask for the Wine devolpers to work on Guild Wars. Also if you don't mind spending $5 a month,get Cedega. I don't use it but my friend does and it works just like on a Windows OS.

---

### Post by Polygon on 2007-08-20
I just got guild wars working in ubuntu today and i say it almost runs perfect.

if you havent already:

in winecfg make sure the audio driver settings are set to alsa, the default is set to OSS

set windows compatibility mode to windows 98

use this command to launch guild wars:

```

WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -dx8 -noshaders -windowed


```

if the above command works, then you can try it with direct x 9 (remove -dx8 from command), but even with my computer i notice that it lags really bad if you take -noshaders off

see if that works

---

### Post by buttons on 2007-08-20
Sigh.  Someone really needs to sticky the GW launch command, or at least force people to read that "How I got Guild Wars Working" thread.  Even if this works...read it anyway.
```

&#9484;&#9472;(buttons@freyja:pts/0)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~)&#9472;&#9488;
&#9492;&#9472;(09:55:%)&#9472;&#9472; cat bin/gw                                        &#9472;&#9472;(Mon,Aug20)&#9472;&#9496;
#!/bin/sh
export WINEDEBUG=-all
wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -dx8 -noshaders

```

EDIT: It also works with OSS enabled in winecfg, if you're curious.  The difference in the above command and Polygon's is the nice fullscreen-ness.

---

### Post by Polygon on 2007-08-20
i dont like fullscreen because if guild wars or wine crashes for any reason, good luck killing the application. With windowed mode, you can still open a terminal and type "killall wine"..... but take your preference :D

---

### Post by Tyke91 on 2007-08-20
you guys are gods :)

---

### Post by buttons on 2007-08-20
> **Polygon said:**
> i dont like fullscreen because if guild wars or wine crashes for any reason, good luck killing the application. With windowed mode, you can still open a terminal and type "killall wine"..... but take your preference :D

Hmm.  Odd thing about wine is that it doesn't seem to understand "fullscreen," at least when using xfwm4 as your window manager.  When I'm running wine apps fullscreen I can alt-tab, or better yet ctrl-alt-right (to switch to the next desktop over).  I also set up a key combination for opening a terminal, which seems to work.

It occurs to me that I've never tested this in metacity.  Nor am I likely to, since I don't have it installed :P

I should note that none of this wonderful flexibility ever works in native apps.  For that, you have to ctrl-alt-# to get the main terminal window.

---

