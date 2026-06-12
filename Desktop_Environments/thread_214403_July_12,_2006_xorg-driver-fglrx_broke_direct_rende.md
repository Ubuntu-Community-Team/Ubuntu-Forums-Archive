---
title: "July 12, 2006 xorg-driver-fglrx broke direct rendering...."
date: 2006-07-12
forum: Desktop Environments
---

### Post by JedTheHead on 2006-07-12
Today's (?) update of xorg-driver-fglrx broke my direct rendering with my ATI Radeon Mobility 9200 so now Xgl is broken again :(  

I have tried replacing /usr/lib/libGL.so.1.2 with the older version that worked with the previous xorg-driver-fglrx.  
 
(The version of xorg-fglrx-driver I have now is:  7.0.0-8.25.18+2.6.15.11-3)

Anyone have any idea how to fix this?

Or:

How to find an older version of the fglrx driver (I have no idea what the previous version number was)

and How to keep it from upgrading in the future?

Thanks!!!

---

### Post by MartynM on 2006-07-12
I had a similar thing happen to me (ATI9100) last night. I fixed it by following the instructions in this thread; 

[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

I managed to get limited 3d using this driver, which I never achieved on the standard fglrx.

It might pay to read the whole thread to see if your setup might present any problems with this first, I know jack sh*t about linux really, so just closed my eyed and went for it.;) 

I'm getting fed up with this old ATI card pretty quickly, I'm not going to hit that auto update button quite so hastily next time though, lessons learned!

Good luck.

---

