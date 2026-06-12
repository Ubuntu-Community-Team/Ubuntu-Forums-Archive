---
title: "Stop Nautilus from starting up"
date: 2006-09-04
forum: Desktop Environments
---

### Post by FIONEX on 2006-09-04
Hi,

I switched my window manager to window maker alongside gnome.  The only problem is that I don't want nautilus to start up with gnome.  I tried going to session propeties, removing nautilus from that list, typing gnome-session-save and then logging out.  But when I logged back in, nautilus started up again.

Any ideas will be appreciated.

---

### Post by moore.bryan on 2006-09-04
*have you tried ```
--replace windowmaker
```?*

---

### Post by FIONEX on 2006-09-04
No no, I already got window maker to start up instead of metacity.  It's just that I need nautilus to stop starting up with gnome.  How would I do that?

---

### Post by mitch.c on 2006-09-04
Try this:
```
gconftool-2 --type boolean --set /apps/nautilus/preferences/show_desktop false
```
Or if you prefer a GUI, use gconf-editor to deselect the key.

---

### Post by FIONEX on 2006-09-04
That just hides the desktop but nautilus still starts.

---

### Post by moore.bryan on 2006-09-06
*sorry i misunderstood earlier... in gnome, nautilus is "hard-wired."  i asked a similar question a few months ago, but it died.  when wanting to file manage, you could simply launch whichever program you want (xfe and gnome-commander are nice...)*

---

### Post by FIONEX on 2006-09-08
Just a follow-up.

I did manage to get nautilus to stop booting automatically.  HOWEVER, i have no idea how.  I was just messing around with the session manager and it worked.  I think what happend was that I killed nautilus, then i started it using nautilus --sm-disable .  Then I saved the session.  I hope the helps someone out there.

I hate how all my old threads got deleted when the new version of ubuntu was released!

---

