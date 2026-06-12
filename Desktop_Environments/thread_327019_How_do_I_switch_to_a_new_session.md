---
title: "How do I switch to a new session?"
date: 2006-12-28
forum: Desktop Environments
---

### Post by beanbrain on 2006-12-28
Hello,

I'm finding that the Sessions manager isn't as intuitive as expected. In 6.10, what is the 'Add' button under the 'Session Options' tab meant to do (accessed via System|Preferences|Sessions)?

What I would like to do is save my current desktop, for example with three open terminal windows, and then be able to restore this session either at login time or after login by switching to this saved session.

However, I see no option for switching to a saved session in the GUI or at login (the 'Options' button at login can't have sessions saved under my username because I haven't logged in yet).

How are added sessions meant to be used, if not in the way I describe? I've read documentation in a couple of different places and--surprisingly--don't see this restoration scenario described.

Thanks!

---

### Post by beanbrain on 2007-02-06
Never got a response on this one, but for anyone with the same question searching for an answer, here's what I did.

I was unable to figure out how to restore a session using the session manager UI in Ubuntu, but running 'gnome-session-save' directly preserved my desktop layout of multiple terminal windows. So just hit Alt-F2 to bring up the 'Run' window, then type 'gnome-session-save' and confirm to preserve your session. This won't restore Firefox; however Firefox can restore its own sessions so just shut down Ubuntu while Firefox is still running and then the next time you log in and run it you'll be prompted to start a new session or preserve the previous one.

):P

---

### Post by trippinnik on 2007-02-08
You should be able to type gnome-session-save at the command line and anything you have open will startup automatically when you login.

---

