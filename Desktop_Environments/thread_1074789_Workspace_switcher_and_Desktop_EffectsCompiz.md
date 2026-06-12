---
title: "Workspace switcher and Desktop Effects/Compiz"
date: 2009-02-19
forum: Desktop Environments
---

### Post by clconway on 2009-02-19
I like to set up 4 workspaces in a 2x2 pattern, and keep the Workspace Switcher on my panel. When I enable "Normal" Visual Effects in the Appearance Preferences, the Switcher starts doubling the displayed rows, but the bottom half of the rows don't represent real workspaces. E.g., with 2x2 set as the Workspace preference, the Switcher uses a 2x4 layout, but the bottom half is inactive; with a 4x1 preference, it uses a 4x2 layout; and so on.

I can't find any setting in CompizConfig that controls this. But if I switch the Visual Effects preference to "None", the Switcher goes back to normal, so it obviously has something to do with Compiz... Any suggestions?

---

### Post by maykelmoya on 2009-04-05
See [https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/155438/comments/13](https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/155438/comments/13)

Regards,
maykel

---

### Post by daveola on 2010-12-02
I've seen some fixes that involve manually editing your gconf settings, unfortunately they did not work for me.

What does seem to work, and sheds light on why the bug is caused, is to do the following:

1) Kill compiz (with something like 'metacity --replace')
2) Right-click on the workspace switcher (which probably now looks like a 1x2 box) and select preferences.
3) Change it to 1x1
4) Restart compiz (with something like 'compiz --replace')

It seems that the workspace switcher that compiz uses or puts up in place of the regular switcher is using some of the regular switchers settings.  Ah well.

Interestingly enough I had a workspace switcher in another panel that was working fine, maybe that's why editing my gconf settings didn't work, because they probably need to have different settings.

---

