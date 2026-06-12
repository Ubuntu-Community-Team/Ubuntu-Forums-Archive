---
title: "Mame: sdlmame &amp; xmame.sdl cannot play INCA.ZIP, howto ?"
date: 2008-03-16
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-03-16
Hello,

I compile sdlmame to play inca.zip
this is the file : 
[http://img235.imageshack.us/img235/2912/incaec7.jpg](http://img235.imageshack.us/img235/2912/incaec7.jpg)
 
It has files of this content.

Is there any very well  working MAME, finally  ??

thanks for any ideas of programs


```
/tmp/sdlmame0123$ ./mame  /tmp/inca.zip
am27c512.1 NOT FOUND
2.15e NOT FOUND
m27c2001.3 NOT FOUND
am27c020.4 NOT FOUND
m27c2001.5 NOT FOUND
n82s147n.2 NOT FOUND
n82s147n.1 NOT FOUND
ERROR: required files are missing, the game cannot be run.
Ignoring MAME exception: am27c512.1 NOT FOUND
2.15e NOT FOUND
m27c2001.3 NOT FOUND
am27c020.4 NOT FOUND
m27c2001.5 NOT FOUND
n82s147n.2 NOT FOUND
n82s147n.1 NOT FOUND
ERROR: required files are missing, the game cannot be run.
```

---

### Post by BigSilly on 2008-03-16
Looks to me as though your ROM needs updating. It's a common problem with MAME sadly, whichever OS you choose to use it on. It looks to me as though your ROM has had a better/newer dump and you'll have to find a another version which works with the latest MAME.

---

### Post by frenchn00b on 2008-03-16
> **BigSilly said:**
> Looks to me as though your ROM needs updating. It's a common problem with MAME sadly, whichever OS you choose to use it on. It looks to me as though your ROM has had a better/newer dump and you'll have to find a another version which works with the latest MAME.

thanks 
that's soo sad that it cannot be easy :( 
gp2x how does it work ? they have to get old with trying to find the right roms

---

### Post by BigSilly on 2008-03-16
MAME is not really that easy I agree. You have to pick the version that works with your collection and stick with it really. I myself have stuck with v120.0 because that works really well for me. If I update to a newer version there's a likelihood that it'll break compatibility for me.

It's a very hobbyist-type emulator quite unlike other emus. There's a bit of work involved in keeping up to date with it. For example, a lot of people are looking for it to now begin emulating 3D games like Sega Rally. I myself am very happy as long as I can emulate my old 2D childhood faves, so I won't be updating for quite some time.

I would recommend you do a good search around for an updated INCA or whatever it is you are after, since the dump you have right now of it is outdated. Good luck.

---

### Post by frenchn00b on 2008-03-16
> **BigSilly said:**
> MAME is not really that easy I agree. You have to pick the version that works with your collection and stick with it really. I myself have stuck with v120.0 because that works really well for me. If I update to a newer version there's a likelihood that it'll break compatibility for me.

It's a very hobbyist-type emulator quite unlike other emus. There's a bit of work involved in keeping up to date with it. For example, a lot of people are looking for it to now begin emulating 3D games like Sega Rally. I myself am very happy as long as I can emulate my old 2D childhood faves, so I won't be updating for quite some time.

I would recommend you do a good search around for an updated INCA or whatever it is you are after, since the dump you have right now of it is outdated. Good luck.

I think the problem is certainly that we, linux, should adopt a standard of roms that are windows. 

why not, if that standard is recognized ...

:(

---

### Post by frenchn00b on 2008-03-16
> I myself am very happy as long as I can emulate my old 2D childhood faves, so I won't be updating for quite some time.

what are ya favourite with emulators ?

me, some atari games , like bubble bubble, and nes : zelda icehockey ...

I'd be happy to find non gui emulators that hits working all times ;)

---

### Post by BigSilly on 2008-03-16
> **frenchn00b said:**
> I think the problem is certainly that we, linux, should adopt a standard of roms that are windows. 

why not, if that standard is recognized ...

:(

Not sure what you mean here. The core MAME emulator is exactly the same on LInux as it is on Windows. The roms you would use would be the same. The whole problem with MAME really, is that there *is* no standard for roms. They change all the time, no matter which OS you use. You would have the same problem with your INCA.ZIP using MAME v123 on XP, as you are having here with the Linux version.

Fave games? I seem to spend a crazy amount of time on Capcom beat em ups. Personal favourites are the evergreen Street Fighter 2 Turbo Hyper Fighting, and SFIII Thrid Strike. I'm also quite partial to side scrolling shooters like R-Type etc.

---

### Post by frenchn00b on 2008-03-16
> **BigSilly said:**
> Not sure what you mean here. The core MAME emulator is exactly the same on LInux as it is on Windows. The roms you would use would be the same. The whole problem with MAME really, is that there *is* no standard for roms. They change all the time, no matter which OS you use. You would have the same problem with your INCA.ZIP using MAME v123 on XP, as you are having here with the Linux version.

Fave games? I seem to spend a crazy amount of time on Capcom beat em ups. Personal favourites are the evergreen Street Fighter 2 Turbo Hyper Fighting, and SFIII Thrid Strike. I'm also quite partial to side scrolling shooters like R-Type etc.

I used up to now only zsnes and genesis.

capcom have cute games, I saw, which emulator do you use ?

cpc : target renegate   !!
the music is very particular

Cheers

---

### Post by MaindotC on 2008-03-19
What frontend, if any, do you use for SDL Mame?

---

### Post by DoktorSeven on 2008-03-19
Your problem is twofold, actually:

1) With SDLmame you need to edit /etc/sdlmame/mame.ini to point to a ROM directory; pointing directly to files really isn't the way to do it.  With xmame, there is a commandline switch that you can use to point to the ROM directory; try mame --help or similar to find it.  Then just use the name "inca" (not inca.zip) at the end of the commandline to run it.

2) "inca" depends on a parent ROM, "maya", so you'll need maya.zip in your ROM directory as well.  Your inca.zip looks correct, but it does need maya.zip as well.

---

