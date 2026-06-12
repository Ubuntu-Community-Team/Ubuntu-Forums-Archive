---
title: "Removing Gnome-panel"
date: 2010-07-15
forum: Desktop Environments
---

### Post by newb85 on 2010-07-15
I've seen a few people post a few different ways to remove the  gnome-panel, but none of them seem to work as promised.

Right-clicking a panel and clicking "Delete This Panel" works great for  all but the last remaining panel.  Then the option is ghosted out.

Issuing "killall gnome-panel" only removes the panels for a few seconds,  because gnome-panel is set as a required session component.  In theory,  this could be changed in gconf-editor under  desktop>gnome>session>required_components.  However, no amount  of fiddling with the settings there has allowed me to successfully  "killall gnome-panel".  (I'm running 10.04.  In previous distros, adding  a different non-blank value under "panel" would do the trick, but even  that doesn't work anymore.)

This appears to be a glitch in gnome, but I could definitely be missing  something.

Any thoughts?

---

### Post by kerry_s on 2010-07-16
hmm, strange i did the gconf-editor to use awn & it works fine here.
i'm running 10.04 netbook remix.

i just tried it blank & it works.

---

### Post by nothingspecial on 2010-07-16
```
sudo mv /usr/bin/gnome-panel ~/.panel
```

Then log out and back in

```
sudo mv ~/.panel /usr/bin/gnome-panel
```

if you would like it back

You will loose Alt F1 and Alt F2

---

