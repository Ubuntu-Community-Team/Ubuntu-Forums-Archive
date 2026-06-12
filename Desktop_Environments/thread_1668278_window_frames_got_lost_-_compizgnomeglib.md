---
title: "window frames got lost - compiz/gnome/glib"
date: 2011-01-16
forum: Desktop Environments
---

### Post by altarmp on 2011-01-16
I have been dealing with this problem for at least a few hours and now I seem to have a hint, or a workaround so I'll just post it here for others looking for an answer.

The problem is, each time after playing with my dual monitors (thought probably not the cause) and switching between nvidia twinview and separate windows settings, I had to re-enable compiz, since some of the switching back and fort different dual monitor settings disabled composite effects. Forgetting to save my personalized profile for compiz for a while, I was manually setting some  effects I that I use a lot each time enabling compiz.

I have seen this problem of losing window frames before (thought it was intermittent) but could not replicate the problem, but with my last changes, I bumped into the problem, and old log off - login cycle did not solve the problem, so I thought I lost the window frames for good.

I filed a bug at bugzilla.gnome: [https://bugzilla.gnome.org/show_bug.cgi?id=639653](https://bugzilla.gnome.org/show_bug.cgi?id=639653) and tried different settings with compiz after a while and saw to my surprise that enabling GLib at compiz settings (system-preferences-compizconfig settings) brings back the window frames.

---

