---
title: "totem upgrade - lost ability to play mms"
date: 2006-08-08
forum: Desktop Environments
---

### Post by revoohc on 2006-08-08
Hi all,

I ran in an update for totem, and now when I click on a link to play an mms stream from my online radio station, totem no longer knows how to play it.  I tried re-installing the w32codecs package but no joy.

Any idea what needs to be done to get totem to play mms streams?

Thanks,

Chris

---

### Post by mannheim on 2006-08-10
A recent update to totem (version 1.4.3 now) had the side-effect of removeing totem-xine and installing totem-gstreamer. 

Previously, totem-xine and totem-gstreamer were mutually exclusive, but you could choose either one. In [another thread]("http://www.ubuntuforums.org/showthread.php?t=228299"), it is suggested that the new totem-gstreamer does handle formats previously handled only by totem-xine, but I don't know.

Try checking in Synaptic: is totem-xine installed? Did you have totem-xine before?

If the answers are "no" and "yes", then perhaps the solution is to dig out the totem-xine deb from /var/cache/apt and reinstall it. Does anybody else know the whole story?

---

### Post by gjtoth on 2006-11-18
After trying everything else about loading this and loading that, THIS is the one that worked.  I opened Synaptic; checked to see if totem-xine was loaded (it wasn't); I loaded it.. voila!  I have XM Radio streaming in.  

THANKS!

---

