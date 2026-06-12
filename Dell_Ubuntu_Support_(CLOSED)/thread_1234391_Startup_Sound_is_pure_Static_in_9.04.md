---
title: "Startup Sound is pure Static in 9.04"
date: 2009-08-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jhernandez1270 on 2009-08-07
Hi all,

I just figured this out and since I couldn't find out how to fix this problem on the web, wanted to share.
The sysmptom:
When you log in to Jaunty you get a sound that sounds like static where you usually would hear the Ubuntu login sound.

The workaround:

Under System->Administration->Login Window
Under Accessibility tab
Change the Login Successful:  field from:
 /usr/share/sounds/ubuntu/stereo/desktop-login.ogg 

To

 /usr/share/sounds/purple/login.wav

---

### Post by hariks0 on 2009-10-15
> **jhernandez1270 said:**
> Hi all,

I just figured this out and since I couldn't find out how to fix this problem on the web, wanted to share.
The sysmptom:
When you log in to Jaunty you get a sound that sounds like static where you usually would hear the Ubuntu login sound.

The workaround:

Under System->Administration->Login Window
Under Accessibility tab
Change the Login Successful:  field from:
 /usr/share/sounds/ubuntu/stereo/desktop-login.ogg 

To

 /usr/share/sounds/purple/login.wav

Thank you. But it did not work for me. Actually I had messed gnome and hence deleted .gconf, .gcond, .gnome & .gnome2 from my home folder. Also I installed ubuntu studio 9.04. I don' know which caused the problem

---

