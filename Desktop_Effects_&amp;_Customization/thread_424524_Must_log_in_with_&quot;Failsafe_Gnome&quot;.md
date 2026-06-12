---
title: "Must log in with &quot;Failsafe Gnome&quot;"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by Ender Black on 2007-04-26
If I log in without changing the session to "Failsafe Gnome" none of my start-up scripts execute.  I have scrubbed my sessions start-up list and there doesn't appear to be anything goofy in there.  When I do change to "Failsafe Gnome"... everything works and starts up like I want it to.  Any idea where I should look to unscrew this problem?

---

### Post by drseuk on 2007-05-03
Symptoms:

After upgrading from Edgy 6.10 to Feisty 7.04, a normal Gnome session hangs at the background screen and disk thrashing occurs. If you're lucky, you will be returned back to the login screen. If not, Ctrl+Alt+Backspace may restart the X server. If not, you need to hard reset. I am using the alternate CD on an IBM Thinkpad T20 with limited (5Gb) hard drive space and even more limited free hard drive space.

The failsafe Gnome session works however.

Problem:

For some reason, openssh-client is the problem (not sure why - can anyone enlighten us?).

Solution:

Login to a failsafe Gnome session, start synaptic and reinstall openssh-client. You may also need to remove .ssh from your home directory or directories.

This fixed it for me and now normal Gnome sessions work as they should.

Request: can synaptic be altered so that it doesn't download all requested files first before installing any of them. For people like us with limited hard drive space, it's gaulling to have to clear 1Gb of drive space each time there's an upgrade. This change could be limited to the alternate CD which is obviously aimed at people with limited hardware. We could live with synaptic requiring only, say, twice the space of the largest package being installed in a batch.

---

