---
title: "wine:virtualdubmod, runs well, no codecs found though"
date: 2006-02-14
forum: Desktop Environments
---

### Post by sup on 2006-02-14
Hello, I installed wine and was ableto run Google Earth on it. I decided to move on and try VirtualDubMod (As far as I know there is no alternative for it in linux world). I installed Codec pack AllInOne, without errors, first. Installation of VirtualDuoModwent fine since it has not got any :) (unzip is all you need) and it started without problems as well. However, when I tried to open an avi file (that was using an xvid codec, apparently), I got this message
```
Couldn't locate decompressor for the format 'DIV X'(OpenDIV X)

VirtualDub requires a Vidio for Windows (VFW) compatible
codec to decompress vidio. DirectShow codecs, such as 
those used by Windows Media Player are not suitable.
```

I found an old post in wine mailing list [http://www.winehq.com/hypermail/wine-bugs/2002/06/0279.html]("http://www.winehq.com/hypermail/wine-bugs/2002/06/0279.html") that says I should 
add this :

[drivers32]
vidc.DIVX=DivX.dll


in the ~/.wine/system.ini

However, it is three years old post and config files for wine changed since then, any ideas?

---

### Post by sup on 2006-02-14
nevermind, I just realize system ini is in windows directory, co I added 
vidc.XVID=xvid.dll
to it and it started doing something... blanking my screen, actually:-), I will play with it a little bit more.

btw:for codecpack, msvcp60.dll might be needed

---

### Post by sup on 2006-02-14
windows through winecfg must be set tu xp, at least it seems so, and in preferences of virtualdubmod, directx muset be disabled. then it works as if it were not an windows application - at least from the first look, i might still come into some troubles.

hope this helps someone

---

### Post by MetalMusicAddict on 2006-02-14
Thanx for the info sir. I was *thinkin* of *tryin* to run GordianKnot.  :)

---

