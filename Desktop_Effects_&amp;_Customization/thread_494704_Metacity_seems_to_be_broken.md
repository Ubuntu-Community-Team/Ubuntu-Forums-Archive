---
title: "Metacity seems to be broken"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by Tsuki on 2007-07-07
Somewhat of an embarrassing confession here - I've been playing around with compiz and beryl, but seeing the performance hit of either, I decided to get rid of them.  However, in so doing, I appear to have hosed metacity (and probably also something else).

Openbox loads up fine, but on running "metacity --replace", metacity shows up for a second and then kills X.

However, even with all values of "/usr/bin/metacity" in gconf replaced with "/usr/bin/openbox" (my attempt to load up GNOME with openbox as the WM instead of metacity), GNOME doesn't get very far.  The splash screen appears, but no icons appear along it, and the background stays Ubuntu-brown, with the exception of what looks like a 320x240 grey box in the top-left.

I've tried uninstalling and reinstalling metacity (including the remove-all-settings "Complete Reinstall", but it hasn't helped matters.

Any ideas?

---

### Post by Bosambo on 2007-07-07
Have you tried to restore a previously backed up xorg.conf file?

---

