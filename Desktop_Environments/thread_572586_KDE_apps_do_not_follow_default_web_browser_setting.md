---
title: "KDE apps do not follow default web browser setting"
date: 2007-10-10
forum: Desktop Environments
---

### Post by mfield on 2007-10-10
Hi,

I have been playing with the settings in the KDE Control Center, File Associations, text/html to set up my default browser the way I want it, and I have realized that it doesn't matter what I set there -- links always open in Opera even if I move Konqueror or Firefox to the top of the list of text/html apps (I've tested kmail and akregator).

Am I editing the wrong file type?  Or am I missing something else obvious?  Any ideas on getting this to work?

For what it's worth, I am trying to get kmail to open links in Opera, in a new tab.  I set up Opera with "opera --newpage %u" in the text/html settings, and it should work (it does from a command line), but given that the apps are not reading what's in the text/html settings, I'm not sure what to do.

Thanks for any help with this!
Marc

---

### Post by mfield on 2007-10-15
OK, I solved this one.  In case someone has the same problem:  I had set the default browser to opera in the "System Settings" application (which I must have used when I first installed ubuntu a long time ago, but have not used since then), and changing the association for html files in the KDE Control Center (kcontrol) does not affect the default browser setting in the System Settings Application.  Changing the default browser setting in System Settings to opera -- newpage was what I needed to do.

---

