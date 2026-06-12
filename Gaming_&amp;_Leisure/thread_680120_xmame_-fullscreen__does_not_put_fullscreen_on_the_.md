---
title: "xmame -fullscreen  does not put fullscreen on the whole display"
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-01-27
xmame -fullscreen  does not put fullscreen on the whole display

---

### Post by disturbedite on 2008-01-27
xmame is long dead and super outdated.  please use sdlmame instead.  see my post here for getting it:
[http://ubuntuforums.org/showthread.php?p=4179576#post4179576](http://ubuntuforums.org/showthread.php?p=4179576#post4179576)
(you can use kxmame with sdlmame, there is a link to the kxmame & sdlmame ubuntu packages at my link).

---

### Post by frenchn00b on 2008-01-28
> **disturbedite said:**
> xmame is long dead and super outdated.  please use sdlmame instead.  see my post here for getting it:
[http://ubuntuforums.org/showthread.php?p=4179576#post4179576](http://ubuntuforums.org/showthread.php?p=4179576#post4179576)
(you can use kxmame with sdlmame, there is a link to the kxmame & sdlmame ubuntu packages at my link).

I hope it work too with this problem with xmame: [http://ubuntuforums.org/showthread.php?t=679813](http://ubuntuforums.org/showthread.php?t=679813)

---

### Post by frenchn00b on 2008-01-28
S O L V E D 
Thank you !

```
xmame.SDL mameroms/myrom.zip -fullscreen -jt 5 -ef 5
```

---

### Post by disturbedite on 2008-01-28
xmame-sdl is ***not*** sdlmame.  as i said.  xmame is dead & has been for a long time.  its seriously outdated (mame 0.106).  mame is currently at 0.122 & sdlmame is simply a mame port to sdl.
as i said, sdlmame is the clearly better choice.

---

### Post by frenchn00b on 2008-01-28
> **disturbedite said:**
> xmame-sdl is ***not*** sdlmame.  as i said.  xmame is dead & has been for a long time.  its seriously outdated (mame 0.106).  mame is currently at 0.122 & sdlmame is simply a mame port to sdl.
as i said, sdlmame is the clearly better choice.

Indeed it works great ! I have it running with my freevo box, with 2 gamepad, and tv.

by the way, now, next step, playstation ?
would u know the diff between psx and ps-one, and would oyu know the best way to run playstation from command line ? 

thanks ! 
Mame is really great machine. the games are pretty fine

---

### Post by disturbedite on 2008-01-29
ok, i guess i misunderstood.  great that you are using sdlmame now.  :)

as for playstation, i don't know about command line emulators, but the best playstation emulator imo (& many others') is pSX.  there is an ubuntu package available in [dfreer's repo]("http://packages.dfreer.org/").

---

### Post by frenchn00b on 2008-02-02
> **disturbedite said:**
> ok, i guess i misunderstood.  great that you are using sdlmame now.  :)

as for playstation, i don't know about command line emulators, but the best playstation emulator imo (& many others') is pSX.  there is an ubuntu package available in [dfreer's repo]("http://packages.dfreer.org/").

thanks
when I look zophar, [http://www.zophar.net/unix/psx.html](http://www.zophar.net/unix/psx.html)
the psX code source is not present. Woudl you know whether this psx is the epsxe ? it looks not. EpsxE has already a frontend but I heard it was buggy.

I try to get this psx and psxfrontend you talk, as source code... to get compile it.

this link you gave rocks;
it has even ubuntu and debian repos. very great guy !
i got the source: [http://www.zophar.net/unix/Files/PcsxSrc-1.5.tgz](http://www.zophar.net/unix/Files/PcsxSrc-1.5.tgz)

--edited

---

