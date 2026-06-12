---
title: "Gnome desktop sessions"
date: 2007-05-04
forum: Desktop Environments
---

### Post by sebbouckaert on 2007-05-04
Hi,

I used to work with KDE, Kubuntu 6.10. After the Feisty release I did a fresh install of Ubuntu 7.04, and thus moved (back) to Gnome for different reasons.

One of the differences I noticed is that when I logged out (or rebooted) in KDE it would present my desktop in exactly the same state as I left it. Apps like Firefox, Thunderbird, Kopete etc. would start up by themselves, presenting me an identical desktop situation as how I left it last session.

In Gnome/Feisty this seems not the case. Except for Firefox (which asks if a want to restore, or start a new session) apps like Gaim or Skype, who would be present in my panel during the previous session are not there anymore. Is this normal Gnome behavior?

---

### Post by ohgod on 2007-05-04
I believe you can accomplish this like so (but haven't tried it myself):

System->Preferences->Sessions

Then, in the Sessions window, choose the "Session Options" tab and check the "Automatically save changes to session" box.

---

### Post by sebbouckaert on 2007-05-04
That didn't really work. And now my logoff/shutdown buttons don't work no more, even after reboot :-(

EDIT - fixed. Found topic on forum. Unchecked the 'save sessions' button, then deleted ~/.Gnome2/sessions

after logging back in everything back to normal.

---

### Post by ohgod on 2007-05-04
Yikes.  Sorry about that.  Glad you got it back to normal, though.

---

