---
title: "Problems after installing Beryl with Edgy..."
date: 2007-03-09
forum: Desktop Environments
---

### Post by Umut Ya&#351;ar on 2007-03-09
I installed Beryl on Edgy and started it by terminal but although the red emerald appeared, it did not work and I found these problems;

[B]Xlib: extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
beryl: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Xlib: extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0[/B]

Do I have chance to fix these? I am really new about Linux and maybe I need basic help...

---

### Post by igknighted on 2007-03-09
Looks like you do not have your display drivers installed.  Beryl is not a new user topic. I would get a few weeks/months in learning the basics of the OS, and then look into installing software like Beryl that comes with many many headaches.

EDIT: Do you have an an nvidia card?  ATI cards are not capable of running Beryl without an XGL session, which is difficult to set up porperly.

---

