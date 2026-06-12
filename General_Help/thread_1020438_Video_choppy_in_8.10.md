---
title: "Video choppy in 8.10"
date: 2008-12-24
forum: General Help
---

### Post by pan69 on 2008-12-24
I've just upgraded to 8.10 (gnome) and I noticed that video playback in full screen (1680x1050) is really choppy. I've got my restricted ATI driver enabled and I'm using VLC (what else?) for playback. However, I seem to be getting like 5 fps.

Anyone knows whats going on and a good way to fix this?

Thanks,
Luke

---

### Post by LoneWolfJack on 2008-12-24
are you sure you are using the restricted drivers? check system->administration->hardware drivers. it needs to say "this driver is activated and currently in use" about the proprietary ATI driver.

other then that, are you using compiz? if so, try turning it off.

---

### Post by zika on 2008-12-24
> **pan69 said:**
> I've just upgraded to 8.10 (gnome) and I noticed that video playback in full screen (1680x1050) is really choppy. I've got my restricted ATI driver enabled and I'm using VLC (what else?) for playback. However, I seem to be getting like 5 fps.

Anyone knows whats going on and a good way to fix this?

Thanks,
Luke

System->Preferences->Multimedia Systems Selector->Video->X Window System(no xv).

---

### Post by pan69 on 2008-12-24
> **zika said:**
> System->Preferences->Multimedia Systems Selector->Video->X Window System(no xv).

*Sorry mate. But that menu doesn't exist after a fresh install, at least not on my system.*

Forget that, I could enable it by right clicking the Ubuntu icon in my task bar and enable through 'edit menus'.

Setting the option you mention doesn't make a difference. When I turn off compiz however it all seems to work fine.

So my next question would be, any ideas on how to get compiz and video acceleration working at the same time?

---

### Post by LoneWolfJack on 2008-12-24
there's no fix for the ATI/compiz issue as of yet. 

however, there's a little program that you can use to turn compiz on and off with two clicks (sudo apt-get install fusion-icon). that's as good as it gets for ATI cards atm.

---

### Post by pan69 on 2008-12-24
That's a shame. Well, I wasn't used to having compiz turned on anyway so it'll have to go I guess...

Thanks for your guys help!

---

### Post by zika on 2008-12-25
> **pan69 said:**
> That's a shame. Well, I wasn't used to having compiz turned on anyway so it'll have to go I guess...

Thanks for your guys help!

I have ATI Radeon HD 3650 and compiz on Extra and videos are OK. I had that problem and I think aforementioned switch made it dissapear. I also have newest ATI driver with Catalyst 8.12. I'll go through my notebook for Ubuntu and see what I forgot to mention that helpeed. Try to find any place that mentiones xv and change it to x11.

I see You use VLC so try:```
vlc --vout x11 %U
```Merry Christmas.

---

### Post by pan69 on 2008-12-25
The only thing that makes it accelerated output in fullscreen mode is to select OpenGL rendering within VLC. However, thats choppy in another way in that I see lots of black rectangles.

For now no fancy desktop for me I guess :)

Thanks for your help and merry Christmas to you too!

---

### Post by zika on 2008-12-25
> **pan69 said:**
> The only thing that makes it accelerated output in fullscreen mode is to select OpenGL rendering within VLC. However, thats choppy in another way in that I see lots of black rectangles.

For now no fancy desktop for me I guess :)

Thanks for your help and merry Christmas to you too!

The only reasons I'm keeping Compiz instead of Metacity (that I like very much because its simple) are:

-   I can scroll through workspaces with middle-mouse-button
-   I can make pages in browser in negative (due to bad choice of colors by designer)

If that I had in Metacity I would be in metacity forever.

Edit: there is a site: [http://kb.mozillazine.org/Testing_plugins](http://kb.mozillazine.org/Testing_plugins) and there I've tested all plugins (in Epiphany and in Firefox (in order of priority in use)). The only one that gives flicker while playing video is [http://service.real.com/realplayer/test/](http://service.real.com/realplayer/test/) but even that can be solved. Right-click on the video and choose Video output to be x11 ... works!

Thank You for nice wishes.

---

### Post by andybunted on 2008-12-26
Hi mate,

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1021773](http://ubuntuforums.org/showthread.php?t=1021773)

Made a world of difference to my setup, I'm using an older ATI 9550 myself.

Cheers,
Andrew.

---

### Post by zika on 2008-12-26
> **andybunted said:**
> Hi mate,

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1021773](http://ubuntuforums.org/showthread.php?t=1021773)

Made a world of difference to my setup, I'm using an older ATI 9550 myself.

Cheers,
Andrew.

Thank You very much. It hellped me get 60Hz on my Acer X223wQ monitor (I've put 61 just in case it doesn't get rounded again somehow. I wasn't aware that it was crippled *there* to 50Hz. I'll have to read that thread more than once more. Nevertheless I am a bit confused if refreshment rate even applies to LCD monitor? I think I can see the difference but ... ;)

Did You make any changes in xorg.conf since everything is moved elsewhere by ATI drivers ...? I've found several threads about adding Options to xorg.conf but I haven't tried them yet. Any experience with that?

Changes I've mentioned in my previous post made flicker dissapear from videos in Compiz several weeks ago... this change You proposed does not make them unnecessary.

Have a very good and happy New Year!

P.S. While looking at panel Display Settings in CCSM I noticed that Texture Filter could be set to Fast since ATI Catalyst will do the work and it make a nice change. It almost makes Compiz as fast as Metacity. This way I do not have to give up things I mentioned in my earlier post.

---

