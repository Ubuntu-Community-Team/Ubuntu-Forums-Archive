---
title: "Savage white screen, posted solution does not work"
date: 2007-09-18
forum: Gaming &amp; Leisure
---

### Post by Ripfox on 2007-09-18
[http://ubuntuforums.org/showthread.php?p=1853705](http://ubuntuforums.org/showthread.php?p=1853705)

Does not work for me, makes my screen turn black and the cursor leaves a white trail.

Any one figure this out? Game looks cool.

I have intel i915 graphics.

---

### Post by Vadi on 2007-09-22
I'll go try it out... I'm getting a white screen too. ATI Radeon 7500 here.

---

### Post by Vadi on 2007-09-22
Well, I got the same as you. Heh.

---

### Post by Vadi on 2007-09-22
Oh, here's what the terminal says:

```
vadi@vadi-laptop:~/.Games/SavageFE$ ./savage.sh
System_Init()
Mesa 6.5.2 implementation error: User called no-op dispatch function (an unsupported extension function?)
Please report at bugzilla.freedesktop.org
TexCoord2f: 1
vadi@vadi-laptop:~/.Games/SavageFE$ 

```

I guess that's a problem.

---

### Post by Perfect Storm on 2007-09-22
Tried run ./silverback.bin instead?

---

### Post by Vadi on 2007-09-22
Yeah, same effect.

I think it's that savage is trying to use pixel shaders, looking from some bug reports here and there. My card doesn't have that, and I can't find what option do I need to disable in these numerous .cfg files :(

---

### Post by Vadi on 2007-09-22
Both .sh files point to silverback.bin, anywho.

---

### Post by Vadi on 2007-09-22
I tried graveyard.sh, which launches silverback with "silverback.bin mod graveyard", and it gives me some weird enviroment with trees, I think and such. Hm

---

### Post by Geek506 on 2008-04-25
> **Vadi said:**
> Well, I got the same as you. Heh.

I get the same white screen ... I can hear sound and mouse clicks fine. Need help :-)


Thanks

---

### Post by Vadi on 2008-04-25
Upgrading my video card did it. Maybe yours is too old too?

---

### Post by Geek506 on 2008-04-28
Ok ... installed game, created icon in Games Menu, loaded game ... have sound, but then it goes to a white screen. I have to ~ and 'exit'. Read lots of comments here on the boards, but I was wondering is there some way to disable pixel shading in a config somewhere? My vid card doesn't support it. Need help, thanks

When I ~ out of that white screen I see that "attempt to compress texture failed ... blah blah blah ... *.tga" Is there something in my startup.cfg file I can tweak?

---

### Post by Vadi on 2008-04-28
Don't think you can disable it. Savage 1 is a pretty graphics demanding game, Savage 2 is even more.

---

