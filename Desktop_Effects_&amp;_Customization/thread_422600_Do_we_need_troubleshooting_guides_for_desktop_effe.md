---
title: "Do we need troubleshooting guides for desktop effects?"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by Gillingham on 2007-04-25
HI all, I've just managed to get Beryl working under Feisty with a Nvidia card.  I followed the guide mentioned by Pricechild in the post ["One thread to rule them all v2: Beryl & Official Compiz"]("http://ubuntuforums.org/showthread.php?t=272104"). It was a bit of a pain troubleshooting, but there were plenty of similar posts here with people having problems.  Are we in a position to actually build up a list of things to try when we encounter problems?

My problem was that the window decorations weren't showing up, so I had no title bar and the gnome-terminal was a plain white box (although thankfully xterm worked fine).  I found two ways of fixing this:

1) append the following to your /etc/X11/xorg.conf in the “Device” section:

```
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

```

and 2) changing the rendering path (under advanced Beryl options) to copy (from automatic) seems to have worked.

(I think that 1) is probably a better solution than 2)).

---

### Post by Robynsveil on 2007-04-25
> **Gillingham said:**
> ...and
 2) changing the rendering path (under advanced Beryl options) to copy (from automatic) seems to have worked.

(I think that 1) is probably a better solution than 2)).
Hi Gillingham, where in the Beryl settings manager does one change the rendering path to copy from automatic? or is that done in some config file? Oh and BTW, that setting change in /etc/x11/xorg.conf worked a treat. Thanks for including the path - I'm new to Linux and Ubuntu and it sure helps to be shown where these files are!

---

### Post by Gillingham on 2007-04-25
> where in the Beryl settings manager does one change the rendering path to copy from automatic? or is that done in some config file?

Sorry I didn't explicitly say.  It isn't under the beryl settings manager.  It is in the menu you get from clicking on the red "beryl" jewel, one of the options is "advanced Beryl Options" and changing the rendering path is (I think) the  top item in the sub menu.

---

