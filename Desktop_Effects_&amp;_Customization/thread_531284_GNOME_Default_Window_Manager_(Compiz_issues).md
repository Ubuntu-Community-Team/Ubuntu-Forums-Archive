---
title: "GNOME Default Window Manager (Compiz issues?)"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by Tsuki on 2007-08-21
Quick question - how does one set the default window manager in GNOME?

I've installed the latest Compiz Fusion out of Amaranth's repo, and I'd like it to run with GNOME instead of metacity.  All the posts I've read seem to suggest System>Preferences>Desktop Effects>Enable, but this doesn't seem to work properly.  The screen flickers as though it's doing something useful, and it removes my metacity borders, but doesn't seem to add compiz ones.

"compiz --replace" works fine, and I can run that on startup from the Session Manager, I'd just rather not have the few seconds of not windowing anything properly before compiz finally loads.

My thought was to find wherever the default WM is specified and change that, though if there's a better way of doing it please let me know!

---

### Post by ddrichardson on 2007-08-22
This is controlled by .xsession and .xinitrc locally, or by the same files  without the periods in /etc/X11

Check man pages for more information.

---

### Post by kevmitch on 2008-03-22
I guess this thread is kind of old, but it was driving me insane how non-trivial it is to do this "the right way" in spite of the fact that it's such a common task. I managed to dig this up on some forum somewhere:
```

echo export WINDOW_MANAGER=/usr/bin/compiz > ~/.gnomerc

```

---

