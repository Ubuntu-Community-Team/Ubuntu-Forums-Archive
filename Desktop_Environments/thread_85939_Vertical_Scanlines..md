---
title: "Vertical Scanlines."
date: 2005-11-03
forum: Desktop Environments
---

### Post by celluloid on 2005-11-03
Hey guys, I've just re-installed Breezy from CD, "server" install and apt-get xubuntu-desktop for a minimal system.

Problem is I cannot seem to set my Monitor's refesh rate correctly. I have tried everything from editing xorg.conf with the Vertical and Horizontal values I found for my monitor too using a modeline generator.

XFCE shows my monitor running 1024x768 @ 85, however all the other resolutions show at 86khz?

Monitor worked fine running Hoary with only XFCE, even with Hoary apt-get upgraded to Breezy but not with Breezy fresh intsll.Wondering if anyone knows anything that could be causing this, I am getting very small 1-2mm "scanlines" horizontally across the screen, causing everything to have a flicker like effect and text is hard to view.

My monitor is Hewlett Packard HP71.

Thankyou.
Grant.

---

### Post by celluloid on 2005-11-03
Anyone know what to try? At 800x600 @ 86 the picture is clear and the "scanlines" are gone, So I need to change from 1024x768 @ 85 to 86khz.

Can't figure out how to do this in XFCE.

---

### Post by celluloid on 2005-11-04
Guess no one knows how to do this? Sorry but it's really straining on the eyes and annoying, need some help.

---

### Post by celluloid on 2005-11-05
Need help, quick.
This little annoyance is turning into a major pain right now. Effecting my whole computing experience.

I have searched everywhere for some extra hints but nothing can be found.
Somebody please help me, I'm sure someone here must know how to solve this problem, Even specifically change the refresh rate from 85khz to 86khz in XFCE?

---

### Post by heimo on 2005-11-05
In xorg.conf, try changing VertRefresh to 86 or adding a new modeline. Some instructions:
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

