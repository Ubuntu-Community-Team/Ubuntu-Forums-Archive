---
title: "[SOLVED] Customizing themes makes system choppy?"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by Onay on 2008-04-12
Whenever I customize some part of ubuntu (GDM login screen, GTK theme, etc.) I find that there are things that do not work well and make the system very choppy. For example, I installed a GDM theme from gnome-look.org, but whenever I start up the computer, I can see it loading the originally login screen (that neutral orange color) before the GDM theme I installed shows up. This makes the computer looked "riced" out in a sense that although it is customized, it's still very rough around the edges.

I know that I cannot complain about it not being perfect since everything is all free. I thank everyone who has worked on making ubuntu such an amazing OS, becoming my primary OS as well, but there are still little things that bother me about it that I cannot wait to get fixed.

So how do I make these custom themes more "streamline" or better "fit and finish" with the OS?

---

### Post by CarpKing on 2008-04-12
Is the orange/tan color solid?  If so, that's a bug that affects anyone who tries to change it.  They hardcoded that color when it's intended to be customizable.  I don't know if they fixed it in Hardy, but I would guess that they probably did considering how many people reported it.  I think there's a workaround for Gutsy, but I don't know it off the top of my head.  Do some searches for "GDM" and "brown" and it will probably come up.  

As for other theming aspects, the only thing I can think of is that they might be using a lot of system resources.  For instance, the pixmap GTK engine is a lot hungrier than something like Clearlooks, and I've heard of it slowing things down.  Large icons that must be resized can have a similar effect.  I think the only way to avoid trouble is to make the filesizes smaller, even if the package gets bigger (i.e. premaking icons in various sizes rather than only including the largest).

---

### Post by KOTAPAKA on 2008-04-12
are you talking about the splash screen (the orange thing)? you can change it - I remember changing it to black ( as my theme was black). you can put a picture as well. have a look around the forum - there is a lot about splash screens. i was using 7.10 by the way and I encountered no bugs whatsoever.

---

### Post by Onay on 2008-04-13
Yeah I fixed the splash screen thing. On the themes problems, I think my main issue was weak engines or very complex themes (all dark ones, etc.) I found a nice green theme similar to ubuntu human and everything is very nice. Thanks guys for all the help

---

