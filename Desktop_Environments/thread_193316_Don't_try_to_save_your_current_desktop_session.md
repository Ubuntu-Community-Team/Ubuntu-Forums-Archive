---
title: "Don't try to save your current desktop session"
date: 2006-06-09
forum: Desktop Environments
---

### Post by marcw on 2006-06-09
I am copying a bug I posted to Launchpad to hopefully save others from what has become my latest headache.  (Btw, Launchpad stinks as a bug reporting tool.)

Bug #49207:
gnome-session-properties is quite broken

In an effort to workaround the lack of "Save Current Setup" check box on logout - which I understand has already been reported - I checked the "Automatically save changes to session" checkbox in gnome-session-properties to save my current desktop. And voila! On my next reboot my desktop looked like I wanted it to.

But to my dismay and disbelief this workaround introduces yet another bug which I have not specifically seen reported. After making sure my desktop was as I wanted, I then unchecked the "Automatically save changes to session" checkbox. But on the next login I was presented with an open gnome-session-properties window AND an open Nautilus. Neither of these was open when I logged out.

This behavior does not happen when the "Automatically save changes to session" checkbox is checked, only when unchecked. I don't wish to leave this check box perpetually checked nor do I wish to have gnome-session-properties and Nautilus open up every time I log in. But it now appears I am stuck with one or the other.

This is 100% reproducible on 2 different machines.

Note: the original reporter indicated the bug was in package 'gnome-session2'; however, that package was not published in Ubuntu.

---

### Post by jelofson on 2006-11-13
Agreed. I have the exact issue with mine. What I have done is this:
Alt+f2 then type gnome-session-save and that will save the current set up. Make sure your session is as you like it. After that, you should be able to remove the checkbox under auto save session and the two windows shouldn't come up. That worked for me. Let me know if that also works for you.

---

### Post by JurB on 2006-12-21
> **jelofson said:**
> Agreed. I have the exact issue with mine. What I have done is this:
Alt+f2 then type gnome-session-save and that will save the current set up. Make sure your session is as you like it. After that, you should be able to remove the checkbox under auto save session and the two windows shouldn't come up. That worked for me. Let me know if that also works for you.

Thank you, that worked for me.

---

