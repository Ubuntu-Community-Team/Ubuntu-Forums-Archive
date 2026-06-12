---
title: "Screensaver on synergy client doesn't start on KDE"
date: 2008-12-22
forum: Desktop Environments
---

### Post by KjetilK on 2008-12-22
Hi all,

I have a bunch of different Hardy systems and I use synergy between some of the boxes. It works great, except that the screensaver on the client machines never starts (and thus, power save doesn't kick in either). It seems that the default behavior of Synergy is that the client should get the screen saver synchronized with the server, but it seems this doesn't happen, and I find nothing to indicate why. I've find many who say that this works great with xscreensaver, but nothing on how well it works with KDE.

Has anybody gotten it working on KDE, and if so, how?

---

### Post by KjetilK on 2009-01-16
Now, I have verified that I can start the screensaver manually on the client machine, and it will also enter power save. So it just seems like there is a signal that is never sent to the client or something...?

---

### Post by Rohan Kapoor on 2009-10-09
I also have the same problem on 9.04 with Ubuntu! Any ideas?

---

### Post by KjetilK on 2010-02-28
Actually, it seems like it depends on which computer is started first at times. It still baffles me, as the display dims, so clearly it has a notion of not being in use, but no screensaver goes on...

---

### Post by Rohan Kapoor on 2010-05-01
> **KjetilK said:**
> Actually, it seems like it depends on which computer is started first at times. It still baffles me, as the display dims, so clearly it has a notion of not being in use, but no screensaver goes on...

I can confirm that the problem is that there is no support for either gnome-screensaver or kde-screensaver. Synergy is only sending the signal to xscreensaver which none of us are actually using anymore.

The [synergy+ project]("http://code.google.com/p/synergy-plus/") is working on a fix that will be released in one of their updates.

---

### Post by KjetilK on 2010-05-03
Thanks a lot for the update!

---

### Post by Rohan Kapoor on 2010-05-16
> **KjetilK said:**
> Thanks a lot for the update!

To those of you who are looking for the exact information.

Here is a link to the synergy+ thread

[http://code.google.com/p/synergy-plus/issues/detail?id=112](http://code.google.com/p/synergy-plus/issues/detail?id=112)

---

### Post by KjetilK on 2010-05-19
Yup.

BTW, I solved (i.e. worked around) half of my problem by installing kscreensaver-xsavers, and by choosing an xscreensaver in the control panel. AFAICS, this also enabled locking.

It did not solve the most important part of the problem though, getting it into powersave. If someone has a workaround for that, it would be great.

---

### Post by Rohan Kapoor on 2010-05-20
> **KjetilK said:**
> Yup.

BTW, I solved (i.e. worked around) half of my problem by installing kscreensaver-xsavers, and by choosing an xscreensaver in the control panel. AFAICS, this also enabled locking.

It did not solve the most important part of the problem though, getting it into powersave. If someone has a workaround for that, it would be great.
You see, I'm on gnome and as far as I can tell, there is no corresponding package and I'm not switching to KDE just for this.

I would think powersaving would come straight up if you can get it to lock/unlock all at once.

---

### Post by KjetilK on 2010-05-22
Yeah, I can see that it is not worth switching just for this. I did some looking into DBUS, and it would be the right thing to use for KDE. I was of the impression that DBUS also played a significant role in GNOME, but apparently not. Anyway, I think it would be a significant contribution to this problem to have a look at what role DBUS plays in GNOME.

---

