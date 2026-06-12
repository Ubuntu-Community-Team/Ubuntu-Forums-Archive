---
title: "GDM: &quot;could not apply the stored configuration for monitors&quot;"
date: 2017-09-29
forum: Desktop Environments
---

### Post by stlu on 2017-09-29
Hello there,

I wanted to share a solution to an annoying problem which I could not find an answer for.  When my system boots, and the graphical login screen comes up (gdm) I get a pop-up message saying "could not apply the stored configuration for monitors."  I searched the web and I got TONS of results saying to remove $HOME/.config/monitors.xml, for people who got this error AFTER logging in, but that is useless for me because I have not logged in yet - so the configuration files in my home directory would not be read.  (And the file did not exist anyway).

Finally, I did a search of my whole filesystem for "monitors.xml" and found this: /var/lib/gdm3/.config/monitors.xml.  After removing it and rebooting, the annoying pop-up didn't happen anymore.

I hope this helps anyone searching for this problem at the login screen.

---

