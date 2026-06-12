---
title: "Firefox in Linux"
date: 2007-04-10
forum: Desktop Environments
---

### Post by Anonii on 2007-04-10
Greetings good people of the Ubuntu community, 

Firefox has been a pain in the *** for me. I find it, really bloated. And I also have some major problems with the flash plugin.

First of all, I'm using Gentoo Linux, in a PC with 1GB of Ram, and a processor of 3.2GHz, which is more than enough for my needs. Anyway, so I'm having Firefox, a Konsole with irssi open and Amarok. In Firefox I have 3 tabs open, including one with a flash video. When I'm switching tabs or changing between programs, I get full 3 or more seconds of waiting. Also, in digg.com, I'm getting a HUEG lagfest, taking me a while to scroll, and pressing the links will freeze Firefox for like 2secs..  Is this normal? I mean... I'm getting less freezing in Windows... 

Also, about the Flash Player... 
I'm attaching the info from about: plugins here, before I describe my problem:
> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

So, well... the problem only appears in Flash Videos (like in youtube, metacafe etc.). The videos basicaly freeze. Usually in the second or third second, but sometimes in the middle of it. To fix it, I'll have to kill Firefox and start it again. Also, Flash is really laggy, and makes the whole page much more bloated than normally a flash application would.


Any ideas?

Thanks!

**EDIT: You probably want to move this thread in "General Help" :/**

---

### Post by FuturePilot on 2007-04-10
If I view a page with a lot of flash on it, it is sluggish when scrolling. I definitely find that annoying because in Windows with Firefox, that same page is just as fast as any other page. Rarely have I had a video freeze on me. It has happened but it's very rare. But I've never experienced any lag when switching tabs. It's fast for me. Not sure if that helps you at all, but I'm experiencing some of that same stuff.

---

### Post by jubjubrsx on 2007-04-10
i used to have problems with flash and firefox esp when i tried mandriva, switched to unbuntu problem pretty much dissapeared.........

but on a side note check into swiftfox, i went to that on mandriva and my problems went away. might be a decent solution to try :popcorn:

---

### Post by jem7v on 2007-04-10
jubjubrsx makes what might be a good suggestion!  Swiftfox might do a better job.  I certainly always use it instead of Firefox now.

Still, Flash doesn't seem very optimized for Linux yet.

---

### Post by Anonii on 2007-04-10
> **jem7v said:**
> jubjubrsx makes what might be a good suggestion!  Swiftfox might do a better job.  I certainly always use it instead of Firefox now.

Still, Flash doesn't seem very optimized for Linux yet.

Gentoo's Firefox is like Swiftfox, optimised for your machine. There is no version of Swiftfox for Gentoo, because there is no need for one...

I checked Gentoo's forums, too, and it seems like Firefox is kinda shitty in Gentoo...

---

### Post by jem7v on 2007-04-10
... By jove, you're right.  It Would be optimized, wouldn't it? Smrt.

I suppose you could always try an alternate browser.  (Not really sure what's available for Gentoo.)

In your opinion, is the performance of Gentoo worth the nature of its package management system?

---

### Post by Anonii on 2007-04-11
> **jem7v said:**
> ... By jove, you're right.  It Would be optimized, wouldn't it? Smrt.

I suppose you could always try an alternate browser.  (Not really sure what's available for Gentoo.)

**In your opinion, is the performance of Gentoo worth the nature of its package management system?**

I don't think that this thread is a place to discuss something like that, but believe me the 0,2% speed increase (funroll-loops anyone?) is not the only thing worth it in Gentoo. Portage (the package management system, like APT) is really superior to APT, imo. Configurable as hell, and without some freaking errors that apt-get and aptitude would give me. It also allows you to optimize your machine to your needs, instead of installing everything that comes with the package. This means, that right now, I have a KDE machine, without _any_ GTK libraries and stuff, except from the absolutely necessary to run Firefox, etc. 
Don't get me wrong, I love Ubuntu and it's swiftness. The fast APT, and the awesome community (I'm still here, right?), but well, Gentoo seems better for me, at least right now, when I can afford spending hours compiling applications. 

Anyway, I don't think that this is the appropriate place, so I'm moving to the topic. I kinda fixed my Firefox. Kinda = I disabled "Smooth scrolling" and "Autoscrolling", and I installed Firefox all over again, with some different configurations, which made it much faster.
Finally, in Ubuntu I had the exact same problems...

---

### Post by hikaricore on 2007-04-11
This is a little offtopic, but if you'd like a more lightweight mozilla based web browser,
you may want to try out Kazehakase (which is in the universe repos).

```
sudo apt-get install kazehakase
```

---

### Post by lexxonnet on 2007-04-11
I've been using konqueror for about 3 or 4 months now, and find it a fair bit more stable and a lot faster than firefox(except a few pages heavy on javascript). You should probably give konqueror a try... with a little effort, it both looks good, and performs well :)

---

