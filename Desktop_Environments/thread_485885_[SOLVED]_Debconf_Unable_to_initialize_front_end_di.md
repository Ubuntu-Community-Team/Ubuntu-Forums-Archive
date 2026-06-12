---
title: "[SOLVED] Debconf: Unable to initialize front end: dialog"
date: 2007-06-27
forum: Desktop Environments
---

### Post by ajgreeny on 2007-06-27
Every time I update my system with synaptic which I prefer to Adept (ubuntu with added kubuntu-desktop, which I use all the time) I get the error message in the terminal which I have open by default:-

debconf: Unable to initialise frontend: Dialog
debconf: (Dialogue frontend will not work on a dumb terminal, an Emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline

Why is this and what does it mean?  Also, does it matter?  Everything seems to update as it should and all works well, but I'm just curious.

---

### Post by kidders on 2007-06-28
Hi there,

Those messages are the result of your package manager running through its list of ways of interacting with you, in order of preference. Depending on how you launch an update process, it may ask you questions every now and then, or fall back on preset default options, whenever choices have to be made about how to proceed. Nothing to worry about. :-)

---

