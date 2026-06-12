---
title: "Firefox, themes ignored"
date: 2005-11-17
forum: Desktop Environments
---

### Post by GozzoMan on 2005-11-17
Hi all gentlepersons,
   hope this is the right forum for the issue (if not, please let me know).

I just installed Breezy with its Firefox 1.0.7; while Extensions install with no problem at all, when I try to install a Theme (either directly through the net or drag-and-dropping from disk to the Themes Panel) I see it for a while in the themes panel and then, when the download bar complete, the theme entry disappears. Restarting firefox is no use: still no theme entry in the themes panel.

I think it could be some kind of permissions gimmick, since if I go for:

gksudo firefox

and then I install a theme from this instance, it install with no problem at all and restarting it (again with sudo) the theme is correctly used (but of course I do not want to navigate with a root-level browser). In fact, a separated /root/.mozilla/firefox has been created.
If I start firefox again (with no sudo) the theme are again nor used neither displayed in the Themes Panel. A tour of my .mozilla/firefox/... revealed nothing unusual about permissions.

Please note that, apart a few extensions, the flash plugin, thunderbird and gnome-vim install, this is an absolute fresh Ubuntu install. That's rather puzzling.

Any idea? Thank you all.

---

### Post by GozzoMan on 2005-11-19
Well, for anyone that might have a similar problem, I've resolved: for still unknown reasons (but I suspect a drop of the net connection during the first theme installation attempt) in the chrome directory in the profile there were a few empty (i.e. 0 bytes) files with the same name (followed by a progressive number) of the first theme jar I tried to install.

After deleting them, the themes began to install just fine.

Cheers,

---

