---
title: "Failsafe GNOME works, but not fluxbox or GNOME (log files included)"
date: 2006-10-09
forum: Desktop Environments
---

### Post by SgtRauksauff on 2006-10-09
Greetings!

Well,the last few days I've been trying to figure this out on my own, but haven't had any luck.

I used to run Debian Sarge (installed before it was the stable release) with KDE as the desktop environment.

The other day, I modded the sources.list file to point to the CDROM drive, and did an apt-get dist-upgrade using the Breezy CD that I had.

everything seemed to go ok, but then I couldn't get any gui whatsoever. I installed gdm, and fluxbox, and gnome, and through the trail of (EE) messages in the xorg.0.log file, was able to get things to the point where I now have (sort of) a gui environment once more.

Now, trying to log into fluxbox or GNOME gives an error saying that it could not start the session.  However, it will start and run when I use the Failsafe GNOME session.  I thought that it migh somehow be permissions related, and used gdm setup to allow root to log in graphically, but the same error occurs.

looking at /var/log/gdm/:0.log, I get basically one error, the "(EE) Couldn't load XKB keymap, falling back to pre-XKB keymap" error. I haven't been able to make that one go away.  So, since I'm not really up on my log interpretations these days, here are some logs that might point out where I need to fix things.

I've attached four log files to this post,they were really long.


I appreciate any help anyone can direct my way.  I'm going to burn a Dapper CD when I get home, and upgrade this box to dapper tomorrow, if I have the time (can't do it online, since this at work and they don't like me playing with Linux. :(  )

I'm not sure if the problem is stemming from the cross-mojination of Sarge and Breezy, or if it's just an incomplete something-or-other, or what.

Thanks!

--Sarge

---

### Post by SgtRauksauff on 2006-10-09
added attachments to the first post instead of a whole 'nother post.

---

### Post by SgtRauksauff on 2006-10-09
Added attachments instead of another post.

---

### Post by SgtRauksauff on 2006-10-10
Anyone? Beuller?  Page 4 in a day with no replies leads me to wonder if this isn't a futile attempt, and I'll end up having to build the system from scratch!

--sarge

---

