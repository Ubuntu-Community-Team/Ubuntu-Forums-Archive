---
title: "SideCandy gDesklets problem"
date: 2006-10-01
forum: Desktop Environments
---

### Post by T'sora on 2006-10-01
Ok, I'm stumped - I'm having an issue with SideCandy gDesklets when they startup.  

When I start the daemon, it loads the desklets, but they are...smushed to only maybe 10 or so pixels wide, and they don't display any information.  It's just a black box outline.  Clicking on them won't expand them at all, right-clicking and trying to configure them doesn't do anything, and restarts don't work either.

I've played around a bit to recreate the errors, and here's what I can do to cause it:

1~Switching the configuration of the desklet from RIGHT to LEFT while the desklet is expanded to its full area.  To switch to LEFT and have the desklet still capable of expanding and hiding (normal SideCandy behavior), I have to compress the desklet, configure it to LEFT, then expand it again.

2~Any SideCandy desklets that are set to LEFT when the daemon is shut down will start up in the super-smushed way the next time I start gDesklets.

I hope that makes sense...

So it's something to do with having them set to Left - anyone else having this problem or know a fix for it?  I know I could just set them all to Right and not worry, but I'd really like to have them on the left side of my screen!  

I've removed and reinstalled gDesklets with apt-get twice, and cleared the gDesklet-data both times, but that hasn't proved helpful. 

Oh, I'm running Dapper 6.06 and Gnome 2.14.3.

---

### Post by orb9220 on 2006-10-01
What kind of video card and drivers are you using?

---

### Post by T'sora on 2006-10-01
I have an NVIDIA GeForce FX 5200 with the most recent drivers.

---

### Post by T'sora on 2006-10-01
Also - sorry - driver I'm using is 'nvidia'

nvidia-glx     1.0.8762+2.6.1 NVIDIA binary XFree86 4.x/X.Org driver

---

### Post by orb9220 on 2006-10-01
I have fx5200 also running on dual monitors, And have about 4 gdesklets running. Havn't seen that problem myself.

I'll keep my eyes open. Did you search gdesklets on forum ?

---

### Post by T'sora on 2006-10-01
Yup - I dug through every gDesklet post I could find on here, and haven't found a similar problem.  I did find a post from back in May on the gDesklet site about the exact same thing, but there weren't any replies, so I don't know if it was ever resolved.

[http://gdesklets.org/?mod=forum/post&pid=295](http://gdesklets.org/?mod=forum/post&pid=295)

---

### Post by T'sora on 2006-10-02
Anyone else have any ideas?  ](*,)

---

