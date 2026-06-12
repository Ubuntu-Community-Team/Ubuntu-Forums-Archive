---
title: "Xubuntu freezes after entering username/password."
date: 2008-12-20
forum: General Help
---

### Post by diablo75 on 2008-12-20
I got a call from a friend who is running Xubuntu on an old laptop.  He says that the laptop will run just fine (boot wise) up until you get to the login screen.  The login screen works normally, but the moment you finish entering your username and password you're stuck with a solid sky-blue screen and a cursor that won't move, and no hard drive activity.  I'm not sure what to try first...

---

### Post by abn91c on 2008-12-20
if he's installed 8.10 it may be a desktop effects issue, he ca try to log in in recovery then tun off the effects, he may also need to remove compiz or metacity. there are many postings here on how to do the latter.

---

### Post by diablo75 on 2008-12-20
I suppose that is possible.  The laptop only has a 400Mhz processor in it... I wouldn't be surprised if they tried to enable it, they lost their desktop, and forced it off with the power button or something.

I'll remove compiz and see if that does the trick.

---

### Post by diablo75 on 2008-12-20
I've not yet tried removing compiz on that other system (have to wait for him to call me back this afternoon).

While waiting, I installed Xubuntu inside a Virtualbox VM just to experiment with it and noticed that the compiz package is not installed by default.  Would it have tried to install itself somehow if he had been messing with appearance settings?

I also tried to load Xubuntu using the Failsafe Gnome option, and it failed with and error that says "Could not find the GNOME installation.  Try running failsafe xterm session.

There doesn't appear to be a failsafe xfce option available either.

So if Compiz isn't there, and I can't load up a failsafe xfce or any GUI for that matter, which else could I try?

---

