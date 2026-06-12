---
title: "gnome-shell running in openbox session?"
date: 2017-08-28
forum: Desktop Environments
---

### Post by again? on 2017-08-28
Using ubuntu-gnome 17.04 and noticed gnome-shell runs in both my openbox and xfce sessions.
Does gdm3 require gnome-shell to be always running?

---

### Post by #&amp;thj^% on 2017-08-30
Not sure it is necessary but it is new.
> GDM's behavior was changed in 3.16 so that instead of running one X server on the login screen which is then transformed into the user's session, we now start a new X session from within the user's session, which means that we need to start the user's session on another TTY/VT.

Note that when using fast user switching, you effectively got this behavior as well, with each user on a different TTY/VT. We just extended it to the first user to log in as well.
Old Bug reference found here and response by the maintainer: [https://bugzilla.gnome.org/show_bug.cgi?id=747339](https://bugzilla.gnome.org/show_bug.cgi?id=747339)
Sorry I've been offline for a few days.

---

### Post by again? on 2017-08-30
Interesting. Seems gnome devs aren't too concerned about gobblng up resources.
In my my gnome session, gnome-shell goes from 150 to 360mb mem usage just by opening the applications overlay and gnome-shell
uses 100mb in my open-box session.
Switched to lightdm.
Thanks.

---

