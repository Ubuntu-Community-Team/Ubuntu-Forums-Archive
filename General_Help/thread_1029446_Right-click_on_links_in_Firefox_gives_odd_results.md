---
title: "Right-click on links in Firefox gives odd results"
date: 2009-01-03
forum: General Help
---

### Post by Seamyst on 2009-01-03
Right-clicking on links in Firefox (in order to select "Open link in new tab") will sometimes bring up the correct menu.  Other times, however, it takes on a mind of its own - it will assume that I selected "Save file as", or "E-mail file", or try to add the file to AdBlock, or give me the link properties, or other similar actions.  Right-clicking and holding, however, always brings up the correct menu.

This happens on both my home computers - an old Gateway running Xubuntu Hardy and a MacBook running Ubuntu Intrepid.  It does NOT happen on my work computer, which is a Dell running Windows XP.  The extensions are the same on all three computers, so clearly (in my mind) it can't be an extension issue.  I use standard scroll-wheel optical mice on both home computers (and have the touchpad on the MB disabled).

Any ideas on how to fix this problem?  It's not big, but it's annoying.

---

### Post by AlexBellisBrown on 2009-01-03
Known Bug: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295)

---

### Post by Seamyst on 2009-01-03
> **AlexBellisBrown said:**
> Known Bug: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/206295)

That's it, all right.  In the parent bug post, several posters noted that the extension Mouse Gestures worked to fix the problem (possibly only until FF 3.0.5), but I can't find an extension by that exact name in Firefox Addons.  Oh well, I subscribed to the parent bug post, so at least I'll know of any other developments.  Thanks!

---

### Post by AlexBellisBrown on 2009-01-03
No problem at all. I think they mean this Add-on? [https://addons.mozilla.org/en-US/firefox/addon/39](https://addons.mozilla.org/en-US/firefox/addon/39)

---

### Post by Seamyst on 2009-01-05
That's the one, yes.  It seems to be working so far, too.  Thanks!

---

