---
title: "4th generation ipod mounting read only after firmware upgrade"
date: 2009-05-29
forum: General Help
---

### Post by euchrid33 on 2009-05-29
I have a black 8gb 4g ipod, which I've been using with Rhythmbox on Ubuntu 9.04 with no problems until now.  It recently started appearing as being 0 bytes large, possibly as the result of getting unplugged without being unmounted correctly.  I decided to rectify this by restoring it on my friend's Mac, and here my troubles began.

When I did the restore, iTunes automatically upgraded the firmware to the latest version.  The iPod now mounts as read only on Ubunutu 9.04.  I've tried adding songs using Rhythmbox, Banshee, Amarok 2 and gtkpod, all without success.  I've also gone into it using both Thunar and Nautilus, as root (ie by loading the file manager using sudo from the terminal) and neither can change the permissions.  I can see that the ipod is mounting as read only, and when I try to change the permissions they both refuse.

I'm now out of ideas.  I can get to a Windows machine and try to restore it once more using that, but I'm not optimistic, as I'm pretty sure that it was the firmware upgrade that screwed me.  Does anyone know of a way to downgrade that?  Or any other solution?

---

### Post by euchrid33 on 2009-05-29
Sorry, I forgot to mention that the iPod in question is a 4th gen Nano.

---

### Post by euchrid33 on 2009-05-29
Fixed!  I'm not sure exactly how, but it's fixed, and I'll post the rest of it here in case anyone else has the same encounter.

I restored the iPod again, this time on a PC running Windows.  It once more upgraded the firmware, this time with the Windows version.  I also removed it from the PC as soon as it was done, without setting a username or anything like that.  I'm not sure which of these steps made the difference, but it now mounts and loads fine once more on Ubuntu.

I hope that my experience will be useful to someone further down the road.

---

