---
title: "Games on Ati Mobility Radeon X300 Ubuntu 9.04, why some work and why some don't?!"
date: 2009-05-18
forum: General Help
---

### Post by Vorticon on 2009-05-18
Hello,

I've been trying to find an answer, or rather a solution to my problem.
I am browsing through the forums and I see all kinds of posts about my problem with 20 different not-really-solutions.

It seems that old ATI cards aren't supported by ubuntu 9.04.
I'm running 9.04 on an Inspiron 6000 with an ATI Mobility Radeon X300

I can play stuff like OpenArena. I can enable Compiz even on extra everything works fine.

I can't play stuff like Tibia or Graal cause I get errors like this when I try to start.

```
X Error of failed request
```

Why can I run intense games (for my laptop that is) like OpenArena and why can I use compiz, but why can't use simple top-down 2d games like Tibia/Graal/etc... ?

Is there a reason and more importantly a general solution for this problem or doesn't even Ubuntu support older graphics cards anymore?

Thanks in advance

---

### Post by Vorticon on 2009-05-19
bump

---

### Post by rizman on 2009-05-19
The problem does not lie with Ubuntu itself. As you already stated, older ATI cards are not supported anymore by ATI. So Ubuntu 9.04 uses the open source drivers by default.

Those drivers have support for almost everything 2D and some 3D (although 3D is not as good as with the ATI drivers. At least for my card: Mobility X700).

The problem you're facing is related to how the games you want to play are programmed or better, which graphics API they use.

OpenArena might work with OpenGL 1.2 (don't know what they use. Just an example). Thus, if the open-source drivers implement the OGL 1.2 specs for your card, all is well for OpenArena.

Now a simple 2D game like pong can be implemented using the latest and fanciest OpenGL 3.0 specifications, even if it looks like an old DOS game (indeed, using newer graphics API does not necessarily mean that a game looks better). However, if the drivers do not implement OGL 3, well...you're screwed. You won't be playing the simple pong clone.

That is a possible reason why some games work and some don't.

---

### Post by Vorticon on 2009-05-19
So probably, the open source radeon drivers as they are now don't support the OpenGL versions of those games (i'm guessing theyre using version 2).

Is this support ever going to happen and would a temporary solution be to switch to ubuntu 8.04 or 8.10 until it's fixed?

Since they use an older X version i can apply the older ati propriety drivers instead of the open source ones who haven't matured much yet it seems. ?

Thanks

---

### Post by nolliecrooked on 2009-05-19
> **Vorticon said:**
> So probably, the open source radeon drivers as they are now don't support the OpenGL versions of those games (i'm guessing theyre using version 2).

Is this support ever going to happen and would a temporary solution be to switch to ubuntu 8.04 or 8.10 until it's fixed?

Since they use an older X version i can apply the older ati propriety drivers instead of the open source ones who haven't matured much yet it seems. ?

Thanks

you can kinda get better performance from older ATi chips, if you update Jaunty to x.org 1.6.1, but it still **** slow then. sorry man.

---

### Post by Vorticon on 2009-05-19
> **nolliecrooked said:**
> you can kinda get better performance from older ATi chips, if you update Jaunty to x.org 1.6.1, but it still **** slow then. sorry man.

I doubt these games would still start at all if i do that

---

### Post by nolliecrooked on 2009-05-19
> **Vorticon said:**
> I doubt these games would still start at all if i do that

they do, I had to do this for my laptop. I had to ring ATi and speak to their linux guy, who told me I had to update x.org/server-ati/radeon. its quicker than the default jaunty ati open driver, but to be honest, you may wanna wait for canonical to shift their asses on this.

---

### Post by Vorticon on 2009-05-19
> **nolliecrooked said:**
> they do, I had to do this for my laptop. I had to ring ATi and speak to their linux guy, who told me I had to update x.org/server-ati/radeon. its quicker than the default jaunty ati open driver, but to be honest, you may wanna wait for canonical to shift their asses on this.

Thanks for the tip. I'll just wait till it goes into ubuntu 9.04 then... now i installed 8.04, those games i said that didn't work now work again, i'll be happy for the moment.

thanks

---

### Post by nolliecrooked on 2009-05-19
> **Vorticon said:**
> Thanks for the tip. I'll just wait till it goes into ubuntu 9.04 then... now i installed 8.04, those games i said that didn't work now work again, i'll be happy for the moment.

thanks

using the opensource ati driver?

---

### Post by Vorticon on 2009-05-20
> **nolliecrooked said:**
> using the opensource ati driver?

Nah the proprietary one. I'm afraid that when i use the opensource ati driver it'll give the same errors again. I'll test it out when i get back from work :D

---

