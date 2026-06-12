---
title: "Postal2 Screen Resolution problems"
date: 2008-06-01
forum: Gaming &amp; Leisure
---

### Post by psyopper on 2008-06-01
Hi all,

I downloaded Icculus' [Postal2 Multiplayer Only]("http://icculus.org/news/news.php?id=4419") last night. I unzipped it this morning and tried playing it. 

I'm launching it from the terminal in the unzipped folder that I have full access to using 
```

sh postal2

```

I get the splash screen just fine, but once the game launches it goes outside of my monitor's resolution. My monitor is a Phillips 190s, a 19" LCD 1280x1024@60. I am getting the equivalent of an "out of range" on the monitor telling me to change the input resolution to 1280x1024 at 60hz.

I can hear the game in the background, it seems to be running fine otherwise. Is there some sort of switch I can use to specify the resolution? I tried changing the resolution in the <install>/System/default.ini with no luck.

By the way, I CAN play UT2004 on this machine with no problems. My video card is an nvidia Geforce 6200 and I am using nvidia (not XGL) as my rendering method. Also - running Hardy upgraded from Gutsy (upgraded from Feisty).

Any input or advice is most welcomed!

Thanks!!

---

### Post by psyopper on 2008-06-05
bump...

No-one else is even trying the game? Surprising...

---

### Post by Perfect Storm on 2008-06-05
There've been other threads about that problem, but no solution so far.
I guess reporting back to Icculus so he can fix it fast.

---

### Post by psyopper on 2008-06-06
From Icculus via email:

Ryan C. Gordon wrote:
>
>> Is there a fix for this? Is it a simple tweak to the ini's?
>
> Yes.
>
> You have to edit ~/.lgp/postal2/System/Postal2.ini (changing Default.ini in the installation directory usually won't help, since it's only used when Postal2.ini is missing: that is, a new install).
>
> Find this section in the .ini file...
>
> [SDLDrv.SDLClient]
> WindowedViewportX=800
> WindowedViewportY=600
> FullscreenViewportX=800
> FullscreenViewportY=600
> MenuViewportX=640
> MenuViewportY=480
>
>
> ...and make those into values your system can handle.
>
> --ryan.


Haven't had a chance to try it yet though...

Edit: This did fix it. I set my viewport to 1280x1024 and went into the game. Once there I was able to bring it back down to 800x600 and it's working fine now.

---

