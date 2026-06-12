---
title: "gnome-volume-manager not working in fluxbox"
date: 2009-03-02
forum: Desktop Environments
---

### Post by Timtro on 2009-03-02
Hi all,

I'm using Ubuntu 8.04 (up to date).

I'm getting quite frustrated with gnome-volume-manager. When I run gnome, everything works fine. When I'm in fluxbox, and I have

...
/usr/lib/gnome-volume-manager/gnome-volume-manager &
...

in my ~/.fluxbox/startup file, the manager starts up fine, and sits there, but does nothing when I plug in a device. If I kill it, and run it in a terminal, I get no error feedback (or feedback of any other kind), and it still doesn't work.

Interestingly enough, when I started a gnome session, it recognized my USB stick. I switched to fluxbox with the stick still mounted. With GVM running in flux, I pulled the stick out and it appears that GVM unmounted it and removed the appropriate directory from /media.

At this point, I can't help but wonder if there is another dependency that is not mentioned in older tutorials on 'how to use GVM with flux", the gist of which is always 'put it in the startup and voila'.

Thanks in advance for any help you can give.

Best regards,



Tim.

---

### Post by ajgreeny on 2009-03-02
> I'm using Ubuntu 4.04 (up to date).Did you really mean this or was it meant to be 8.04?  4.04 disappeared from the supported distros a long time ago, so you should think about updating if you really have got 4.04.

---

### Post by Timtro on 2009-03-02
> **ajgreeny said:**
> Did you really mean this or was it meant to be 8.04?  4.04 disappeared from the supported distros a long time ago, so you should think about updating if you really have got 4.04.

You're absolutely right :) Sorry about that. I'll edit my post.

---

