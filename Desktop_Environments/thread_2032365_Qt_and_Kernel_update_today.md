---
title: "Qt and Kernel update today"
date: 2012-07-23
forum: Desktop Environments
---

### Post by Tim Prosser on 2012-07-23
Have just applied the Qt and Kernel update released today and KDE now hangs after the graphical login with only a cursor visible.

Is this update broken, or is it something more subtle?

Can't see anything obvious although there are errors about being unable to open pixmaps in .xsession-errors.

---

### Post by mparillo on 2012-07-23
> **Tim Prosser said:**
> Have just applied the Qt and Kernel update released today and KDE now hangs after the graphical login with only a cursor visible.

Is this update broken, or is it something more subtle?

Can't see anything obvious although there are errors about being unable to open pixmaps in .xsession-errors.

My vote: Something more subtle.
After all, it worked for me, and I am no wizard.

---

### Post by Tim Prosser on 2012-07-24
> **mparillo said:**
> My vote: Something more subtle.
After all, it worked for me, and I am no wizard.

Thanks - that's very useful to know - I'll have to start digging, then!

Installed xfce (xubuntu-desktop) and that works fine, so it is definitely some problem with kde.  I'll probably find that the user prefers xfce...I certainly do.

---

### Post by mparillo on 2012-07-24
> **Tim Prosser said:**
> Thanks - that's very useful to know - I'll have to start digging, then!

Installed xfce (xubuntu-desktop) and that works fine, so it is definitely some problem with kde.  I'll probably find that the user prefers xfce...I certainly do.
I might have misunderstood. I am running 'regular' Kubuntu, When I read you installed xubuntu-desktop, I started to wonder if you also had installed kubuntu-desktop. If so, then the 'It works for me' is a little less applicable.

---

### Post by dozch on 2012-07-24
Hi,

I also had problems after this upgrade; after login kde didn't hang but I got a dialog with the error message:

X session: unable to launch "/usr/bin/startkde" X session - "/usr/bin/startkde" not found, falling back to default session.

I couldn't find "startkde" either. (Re-?)installing kubuntu-desktop using aptitude fixed it for me:

```
$ sudo aptitude install kubuntu-desktop
The following NEW packages will be installed:
  kde-workspace-bin kubuntu-desktop 
The following packages will be REMOVED:
  freespacenotifier{u} kdeartwork-style{u} kdeartwork-theme-window{u} kdeplasma-addons{u} kdewallpapers{u} kinfocenter{u} kmenuedit{u} librhythmbox-core5{u} 
  plasma-containments-addons{u} plasma-desktopthemes-artwork{u} plasma-runners-addons{u} plasma-wallpapers-addons{u} sweeper{u} xscreensaver-data{u} 
  xscreensaver-gl{u} 
0 packages upgraded, 2 newly installed, 15 to remove and 0 not upgraded.
[...]
```

Hope this helps.

---

### Post by Tim Prosser on 2012-07-24
> **dozch said:**
> Hi,
```
$ sudo aptitude install kubuntu-desktop
```

Hope this helps.

Thanks very much for that - it did.  This update must have added a new package that wasn't picked up by the normal dependencies.  Should have tried that one before resorting to xubuntu-desktop.  That'll teach me to avoid applying updates late at night..

All working normally now.

PS It *was* a standard kubuntu install - though there must be a package I installed somewhere that conflicts with kubuntu-desktop resulting in its removal.  I suspect this might affect quite a few users.

---

### Post by dozch on 2012-07-25
I am also a bit surprised this seems to have affected only a few; my install is pretty standard...

BTW I installed kubuntu over an ubuntu install, which may explain why I got an error message (though it didn't look like a gtk-dialog)

---

