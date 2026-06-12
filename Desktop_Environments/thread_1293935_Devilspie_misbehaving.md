---
title: "Devilspie misbehaving"
date: 2009-10-17
forum: Desktop Environments
---

### Post by rfLarke on 2009-10-17
I can't get Devilspie to properly do what I want. I have two Devilspie scripts, one for evolution, which works PERFECTLY, and one for Songbird. Unfortunately, the Songbird one does not work how I want it.

It looks like this:

(if (is (application_name) "Songbird") (begin maximize (set_viewport 3)))

For some reason, when I launch Songbird, its icon pops up in the third Workspace switcher, but then Songbird itself comes up in whatever workspace I'm viewing.

The kicker is that depending on how i have my script setup, Songbird ITSELF won't do what I want, but subwindows like its Preferences WILL go straight to workspace 3 and maximize.

So... Can anyone shed some light?

---

