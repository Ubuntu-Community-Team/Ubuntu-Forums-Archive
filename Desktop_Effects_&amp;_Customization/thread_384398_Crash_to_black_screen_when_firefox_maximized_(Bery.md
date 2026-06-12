---
title: "Crash to black screen when firefox maximized (Beryl on fxglr)"
date: 2007-03-14
forum: Desktop Effects &amp; Customization
---

### Post by Greg_G47 on 2007-03-14
I just spent the better part of a day getting Beryl to run on my P IV 2.4gh, ATI radeon 9600SE. I followed the instructions on wiki.beryl-project.org for the install.

My fxglrinfo is normal. Card/manufactured is identified, everything's great.

my /etc/X11/xorg.config has the extra bit at the bottom disabling composites (as fxglrinfo got angry without this).

My shell scripts are identical to those on the wiki. I initially added beryl-manager in my startup but am now running it from the terminal after my XGL session starts as it likes to crash (to a black screen with a pointer) sporadically during boot.

Running beryl-manager from the terminal doesn't bother me. The problem comes when I get the same type of crash (black screen, pointer, blue/white line occasionally in the corner of the screen) when I maximize firefox or swiftfox. Small windows work fine. Maximize button leads to crash (about 80% of the time).

I can't think of what to do with this where it is only occuring sometimes. It seems less frequent when I run beryl-manager in the foreground (without &) from my terminal window and leave that window open. Not sure why that would make a difference but it seems to.

Any ideas on what to do with this?

---

### Post by pdxsam on 2007-04-30
> **Greg_G47 said:**
>  The problem comes when I get the same type of crash (black screen, pointer, blue/white line occasionally in the corner of the screen) when I maximize firefox or swiftfox. Small windows work fine. Maximize button leads to crash (about 80% of the time).



I'm having the same issue here. I'm perplexed  as to what Swiftfox is doing that's pissing off Beryl like that. 

I haven't found any resolution either.

---

