---
title: "xserver-org, virtual screen size and desktop size in Intrepid"
date: 2009-03-11
forum: Desktop Environments
---

### Post by diamondnular on 2009-03-11
Hi all,

I have an old 8.04 Ubuntu box with dual head setup on monitor and TV, and it runs fine. Recently I got a new system, put Intrepid on that and tried to setup dual head. But it seems to me that Intrepid has some differences (or bugs?) that prevents me to setup correctly. The monitor runs fine, but on the TV, the X size is always bigger than the real size of the TV (like [http://ubuntuforums.org/showthread.php?t=209474](http://ubuntuforums.org/showthread.php?t=209474) or [http://ubuntuforums.org/showthread.php?t=379034](http://ubuntuforums.org/showthread.php?t=379034)). Unfortunately adding Virtual in xorg.conf does not help to solve my problem. 

So my main question is: if Virtual is to control Virtual Screen Size, then which will control the X (or desktop) size? Is it Modes, or Modelines? How can I set the desktop size to be smaller than the Virtual Size?

Thanks,

D.

---

### Post by diamondnular on 2009-03-13
Bump!

---

### Post by diamondnular on 2009-03-15
Sorry, my old box runs 7.10, not 8.04.

I think I found, well at least, something. Used another flat monitor as a second monitor, and both desktops showed up just fine. Used the TV only as a main monitor still got the same issue. 

**Conclusion:** somehow the TV was not detected correctly. Trying Modelines did not work, the desktop size was unchanged no matter the parameter of Modelies I used (for example make it narrower or shorter). RandR is not supported with my card (correct me if I am wrong). Trying Virtual still no success (I read from forum that from 8.04, Virtual is not honored anymore (!)).

So there maybe a major change from 7.10 to 8.04 (and 8.10, 9.04) that xorg does not recognize my TV correctly. If Virtual is not honored from 8.04, if RandR not work with most of nvidia card, then **what** to be use to control virtual screen and desktop screen?

Thanks,

D.

---

