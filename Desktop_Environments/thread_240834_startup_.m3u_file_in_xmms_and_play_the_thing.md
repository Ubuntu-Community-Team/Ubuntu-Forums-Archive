---
title: "startup .m3u file in xmms and play the thing"
date: 2006-08-21
forum: Desktop Environments
---

### Post by scottbakertemp on 2006-08-21
Guys,
I would like to have xmms media player auto load a .m3u file (located on my desktop) and play the thing when my PC starts up.  I have added the .m3u file (name and path) to my fstab file but xmms doesn't automatically play the thing; it just loads and sits there.

thanks for all the great information on this site,
-Scott

---

### Post by mistab1034 on 2006-08-21
what do you mean you added it to your fstab? could you give the line?

you could also put a startup item in your gnome-session (if using gnome) the item would just be:

xmms ~/Desktop/filename.m3u

---

### Post by scottbakertemp on 2006-08-22
Thanks for pointing me in the right direction.  The fstab file was actually doing nothing.  I needed the -p option and put in the session startup items like you said.
the line was the following:
xmms -p /etc/media/playlist.m3u

thanks

---

