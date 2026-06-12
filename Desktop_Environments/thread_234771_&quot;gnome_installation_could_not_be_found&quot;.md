---
title: "&quot;gnome installation could not be found&quot;"
date: 2006-08-12
forum: Desktop Environments
---

### Post by avox on 2006-08-12
Soooo... after playing around with AIGLX, removing it cause it was too slow (Radeon 8500), I proceeded to download ATi's latest drivers and install those.  BIG mistake. They hosed my Xserver somehow, and it took the whole day 'til I finally got some graphics back on my monitor.

X started fine (no errors in the log) using the "ati" driver, gdm started fine (?) as I could log in, but after I did ...nothing.  Just a gray screen and a mouse cursor who seemed perfectly happy with all the wide, open space it had to itself.

So, I reinstalled gdm after a purge, ran dpkg-reconfigure gdm more times than I can count, and moved every gnome config folder (.gconf, etc.) into a bkup directory.  NOW, logging into a gnome session gets me this error:  "Could not find the GNOME installation.  Running failsafe xterm instead" or something close.  The only thing in /var/log/gdm/:0.log that gives me pause is an error that it can't open /etc/X11/xserver/SecurityPolicy, a file that just so conveniently does not exist!  Is there a way to generate one?

I've screwed around with fglrx drivers enough to learn the hard way how to fix Xorg, but I'm comparitively new at GNOME outages.  Are there more components to Gnome I should reinstall?  Oh, and you can forget ubuntu-desktop, cause there's a string of dependency problems with evince it won't touch...

UPDATE:  Okay, I can *manually* start gnome-panel, metacity, etc., but I'm still lost as to how to diagnose the problem.  Nothing similar caught my eye at the official GNOME forums, either.

FINAL UPDATE:  I installed KDE so I'd have a gui in case things went wrong (mini-review: some nice effects. cluttered and unwieldly on the other hand.  might reinstall once 4.0 comes out).  Anyways, I completely removed then reinstalled metacity, nautilus, gnome-panel, etc.  Still nothing.  Finally, I read something about sessions somewhere and didn't see it installed.  Et Voila!  gnome-sessions seemed to have done the trick.  At the very least, gdm allowed a normal GNOME session after that.  Hopefully, this'll help someone else.

---

### Post by papacosta on 2006-11-30
I was going nuts with the exact same problem until I read the last line and installed gnome-session. Thanks for putting this post out there :)

---

### Post by see7a on 2007-05-01
Thanks avox for this very useful post, I had the same issue and I followed your steps to install gnome-session but I'm still don't have my login the same as before

Now when I login I see my desktop, then the window displaying different gnome components loading progress (nautilus, panel, ...) but this window only displays the first icon and then stops. After that a shell window is opened, I guess this is because  I used to login to gnome-failsafe before I install gnome-session again, but now I change the session to gnome and still the shell window.

I guess I have some problem in my gnome startup scripts, do you have any idea how can I restore that to default?

Thanks for your time,
Sameh

---

### Post by Skilly on 2007-07-01
SOMEBODY GIVE THIS MAN A MEDAL!!! You won't believe how many hours I've spent over the past few MONTHS trying to sort out this problem after upgrading my 3 year old daughters edubuntu box from Breezy to Dapper. THANKYOU THANKYOU THANKYOU!!!!

---

### Post by LostInBrittany on 2007-09-22
THANKS !!!!

I can't thank you enough, avox. This problem had blocked me for hours, I was just about to reinstall all when I found your thread. Thanks again!!!

---

