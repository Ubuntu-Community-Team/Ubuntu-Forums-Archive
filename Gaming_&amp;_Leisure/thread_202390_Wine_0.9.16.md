---
title: "Wine 0.9.16"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by LordRaiden on 2006-06-23
Just letting you know all know that wine 0.9.16 is out. It has some ddraw/d3d fixes so your games ***might*** run better (or they might break). So far, my Warcraft III TFT experience is a bit smoother (less spawn lag in DOTA).

---

### Post by keithjr on 2006-06-23
Thanks for the heads up!

Would these changes allow for older (very early win85 era) games like Dungeon Keeper to run a little better?  Just curious.

---

### Post by KingBahamut on 2006-06-23
I believe that DK2 runs fairly well under Wine.

---

### Post by keithjr on 2006-06-23
[QUOTE=KingBahamut]I believe that DK2 runs fairly well under Wine.[/QUOTE]

[http://appdb.winehq.org/appview.php?versionId=3696](http://appdb.winehq.org/appview.php?versionId=3696)

Interesting, you appear to be right.  I need to read further into the comments, I suppose.  Oh man, if I can get this working I'll be so happy...

There looks even to be hope for the original DK.  I'll give it a good ol' college try, I suppose.

---

### Post by keithjr on 2006-06-23
What I meant by the above is...would the new changes to the directdraw and d3d settings affect errors like this that I'm getting for DK:

```
keithjr@ubuntu:~/.wine/drive_c/Program Files/dk$ wine c:\\"Program Files"\\dk\\keepd3d.exe
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd4bfb0)->((nil),00000008)
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd60c88)->(0x10024,00000051)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:ddraw:Main_DirectDraw_WaitForVerticalBlank (0x7fd60c88)->(flags=0x00000001,handle=(nil))
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd60c88)->(0x10024,00000051)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:DIB_DirectDrawSurface_Blt Can't handle DDBLT_WAIT flag right now.
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd60c88)->(0x10024,00000008)
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd60c88)->(0x10024,00000051)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:ddraw:Main_DirectDraw_WaitForVerticalBlank (0x7fd60c88)->(flags=0x00000001,handle=(nil))
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd60c88)->(0x10024,00000051)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd60c88)->(0x10024,00000008)
```

---

### Post by TheSandman on 2006-06-23
This update actually BROKE my game.
And now i'm getting the above errors for games i could play before =/

Seems it can't change colour depth. ](*,)

---

### Post by LordRaiden on 2006-06-23
that'd be a regression then. Check sf.net under wine for some older debs. I don't know how well it has been updated recently, but don't get anything older than 0.9.14 imo. I'm actually trying to get Sid Meier's Alpha Centauri to work at the moment. It'd be nice to get that working again.

---

### Post by FredB on 2006-06-24
[QUOTE=LordRaiden]Just letting you know all know that wine 0.9.16 is out. It has some ddraw/d3d fixes so your games ***might*** run better (or they might break). So far, my Warcraft III TFT experience is a bit smoother (less spawn lag in DOTA).[/QUOTE]

Well, it is a good news. I hope that some old rendering software I used it (Terragen) could be easily - and really - usable ;)

---

### Post by leech on 2006-06-25
[QUOTE=LordRaiden]that'd be a regression then. Check sf.net under wine for some older debs. I don't know how well it has been updated recently, but don't get anything older than 0.9.14 imo. I'm actually trying to get Sid Meier's Alpha Centauri to work at the moment. It'd be nice to get that working again.[/QUOTE]

You do know that Alpha Centauri has a linux native version right?

Leech

---

### Post by ELD on 2006-06-25
Who wants to pay extra for a linux version when they have the windows version :P

---

### Post by keithjr on 2006-06-25
[QUOTE=ELD]Who wants to pay extra for a linux version when they have the windows version :P[/QUOTE]


Usually you do not need to.  There is often a package that will install the game natively but simply requires data from the game CD.

---

### Post by ELD on 2006-06-25
Could you point me to it, as i have yet to see one.

I know the game is available from tuxgames for linux but i have yet to see a installer.

---

### Post by obey43 on 2006-06-25
this version actually made CS:Source work for me finally.

---

### Post by arizonagroovejet on 2006-07-06
[QUOTE=KingBahamut]I believe that DK2 runs fairly well under Wine.[/QUOTE]

In my exeperience it runs much better under Wine than it does under Windows XP. :D 

Under Wine the default hand image is a bit messed up, there are occasional sound stutters and the cut scene movies don't play. However it doesn't crash all the freakin' time rendering the game playable only with a lot of patience and saving every few minutes like it does for me under XP

I get the sound stutter problem under XP too and the missing cut scene movies may be due to having to use a no-cd patch to play under Wine.

---

### Post by keithjr on 2006-07-06
Whenever I try to get DK2 to run in wine I get errors that it cannot change the BPP.  It is rather annoying and, as far as all my searching has shown, completely unsolvable.  Shucks.  I've pretty much given up on wine, could not get anything running at all.  Native games (TA SPRING!) are really my only recourse, that or installing windows 98.

---

### Post by LordRaiden on 2006-07-06
[quote=keithjr]Usually you do not need to.  There is often a package that will install the game natively but simply requires data from the game CD.[/quote]

How would I do that?

---

### Post by keithjr on 2006-07-06
[QUOTE=LordRaiden]How would I do that?[/QUOTE]


This really depends a great deal upon the game and the distro.  For example, [here ]("http://gentoo-portage.com/games-action/heavygear2")is a gentoo portage package for heavygear2.  Back when I ran gentoo, I simply installed that package and used the CD to finish the installation when it was called for.  I'm sorry, I don't have much experience with other native games.  You'd have to find a debian package somewhere, if one existed.

---

