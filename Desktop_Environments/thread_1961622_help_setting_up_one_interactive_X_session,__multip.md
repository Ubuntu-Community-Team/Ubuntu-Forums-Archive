---
title: "help setting up one interactive X session,  multiple non-interactive"
date: 2012-04-19
forum: Desktop Environments
---

### Post by trk204 on 2012-04-19
I have a question about setting up a dumb X display on unused videocard outputs.

What I'm trying to do,  is keep the original X setup for the default display that the user is always logged into.  These are generally single display systems with dual output videocards.  (but we've started getting some quadro nvs450 4 head cards now).  I would like to be able to hang a monitor off one of the unused outputs.  Run 3 or 4 apps with provided geometry to display on the monitor,  so no WM/DE required.  The apps are self updating so no user interaction is needed (for security reasons this is DEF required).

In my head,  I would imagine running a second instance of X,  as I do not want to have the dumb display affected by logins/logouts of the primary display.  Just display the selected apps until powerdown (or runlevel change or whatever faculty to control it)

I'm just not sure how or if it's possible.  Seems completely doable,  but my xorg-fu is not as strong as it should be.

FWIW this will be on various sqeeze and maverick + boxes.

---

