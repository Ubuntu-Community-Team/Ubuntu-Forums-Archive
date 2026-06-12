---
title: "inactivity time make Ubuntu not respond!!"
date: 2005-07-26
forum: Desktop Environments
---

### Post by unrealdark on 2005-07-26
Hi.  When I am working with Ubuntu I have no problems.  Everything is perfect.  But when I leave it working at night (emule or anything) is hung totally.  What could be the problem?

---

### Post by Kitty on 2005-07-26
[QUOTE=unrealdark]Hi.  When I am working with Ubuntu I have no problems.  Everything is perfect.  But when I leave it working at night (emule or anything) is hung totally.  What could be the problem?[/QUOTE]
 Do you have a laptop?

---

### Post by unrealdark on 2005-07-26
No....   No laptop

---

### Post by Ruskie on 2005-07-26
[QUOTE=unrealdark]No....   No laptop[/QUOTE]
 Check your screensaver settings. In my experience, many of the randomly selected screensaver that come with the standard installation put heavy load on the system...

---

### Post by unrealdark on 2005-07-26
Yes random screensaver enable. But only this week I got this error after an apt-get upgrade (no strange repositories)...   I have disabled screensaver. I'll tell you tomorrow.
Thnx......     :smile:

---

### Post by az on 2005-07-26
[QUOTE=Ruskie]Check your screensaver settings. In my experience, many of the randomly selected screensaver that come with the standard installation put heavy load on the system...[/QUOTE]

Especially if you have certain videocards, the GL (3d) screensavers can make you system hang.

File a bug report, if there is not already one.  This is a bug in X, not in xscreensaver.

bugzilla.ubuntu.com

---

### Post by unrealdark on 2005-07-27
Yes, screensaver was the problem.. I disabled it yesterday and no freeze problem! 
Thnx all for your support! 
:grin:

---

### Post by girijesh on 2007-11-15
do u mean to say that screensavers should not be used in ubuntu. Does it not make the distro an incomplete distro?

after so many releases why can't this problem be addressed?

---

### Post by mcduck on 2007-11-16
> **girijesh said:**
> do u mean to say that screensavers should not be used in ubuntu. Does it not make the distro an incomplete distro?

after so many releases why can't this problem be addressed?

No. But if you haven't got a 3D card and drivers that can handle 3D, you should not use any screensavers that use OpenGL or 3D. But using any other screensaver is fine.

And the problem is that you don't either have a graphics card that can handle OpenGL, or ypu don't have proper drivers for it installed. It's not a problem Ubuntu developers can fix, either you just need to install the driver, or if one doesn't exist the manufacturer of the graphics card should make one.

(Besides, nobody _needs_ a screensaver any more. Modern displays don't need that kind of protection..)

---

