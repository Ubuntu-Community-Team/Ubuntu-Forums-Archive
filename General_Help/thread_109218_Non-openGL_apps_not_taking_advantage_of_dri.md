---
title: "Non-openGL apps not taking advantage of dri?"
date: 2005-12-28
forum: General Help
---

### Post by sammal on 2005-12-28
Hi,

I have a (64-bit acer) laptop running breezy and mobility radeon 9700 from ati. I have installed the latest binary drivers from ati and have DRI enabled (according to x.org log). I'm also informed of radeon driver being loaded by fglrxinfo and get almost-acceptable frame rates on fglrx_gears. 

The problem is that non-opengl apps are really really slow, and I have a strong feeling they are not using DRI, even though it is enabled but sending all pixel data through x server. For example full screen gnome terminal is really lagging in updates, and moving large windows is all-but-pleasant. Is this even possible and what could be a solution? 

Cheers,
Lasse

---

### Post by sammal on 2005-12-29
Replying to my own message just in case somebody wonders the same. The problem with the terminal screen updating seems to actually be a gnome terminal problem. With bitmapped fonts xterm is flying. I reconfigured my fonts so that gnome terminal can also find the bitmapped fonts, but the speed remained the same never the less. So, for sluggish gnome terminal one solution is not to use it and use xterm instead. I've understood this has to do with gnome terminal antialiasing the fonts but it seems to also be slow on bitmap fonts too. Hmm.

Cheers,
Lasse

---

### Post by el3ktro on 2006-01-12
I think this is general a X problem. I have an Nvidia card, and antialiased fonts are really slow here in KDE. When I turn antialiasing off, I see an incredible speed improvement. I hope this gets fixed in the near future, it's really not very pleasant. Well perhaps the new XGL server will help here - everything would be rendered using OpenGL then.

Tom

---

### Post by Cynix on 2006-01-12
I just spent the past few days trying to get the fglrx drivers working in ubuntu, only to find out that instead of using the driver files directly from the ATI website you use apt-get to retrieve the ones in the ubuntu repositories ([https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)) everything works fine first try. Wierd, but now I get both fast 2D accelaration and Ut2004 runs pretty near what I'd expect under windows. I'm especially pleased as it's an X850XT, and relatively new hardware is often unsupported under Linux.

Hope that helps!
L8rz!
Cynix

---

