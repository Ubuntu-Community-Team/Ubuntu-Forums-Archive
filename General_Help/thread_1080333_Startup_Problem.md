---
title: "Startup Problem"
date: 2009-02-25
forum: General Help
---

### Post by Silabus on 2009-02-25
I'm having a problem on startup. I get to the login screen and login just fine, but after that it seems like gnome doesn't load. I'm just stuck at a blank brown screen. Any ideas on what the problem could be? I'm running 8.10 by the way.

---

### Post by stim on 2009-02-25
Did you change something prior to encountering this error?

From the login screen, try clicking the "sessions" button/list on the bottom of your screen and logging in with the "failsafe" session. As a last resort, reconfigure X from a command prompt (which I believe you can also find in the sessions menu.

```

sudo dpkg-reconfigure xserver-xorg

```

---

