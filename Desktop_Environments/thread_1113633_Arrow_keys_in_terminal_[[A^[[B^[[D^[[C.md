---
title: "Arrow keys in terminal: [[A^[[B^[[D^[[C"
date: 2009-04-01
forum: Desktop Environments
---

### Post by Nathanael Culver on 2009-04-01
I'm sure this is a simple matter of flipping a configuration switch somewhere, but I can't find it.

I'm running Intrepid with Gnome and my arrow keys don't work in any of my terminal apps -- gnome-terminal, PowerShell, MXRVT, Terminator. Instead I get [[A^[[B^[[D^[[C, etc. How do I get those puppies to behave?

--Nathanael

---

### Post by Therion on 2009-04-01
Not 100% sure this is what you want, but if you open a Terminal and click on Edit/Profile Preferences and then the Scrolling tab, you adjust some things there.  
My arrow keys are set to scroll through a command history, is that what you want them to do as well?

---

### Post by Nathanael Culver on 2009-04-01
Thanks for the reply, Therion, but I've solved it.

Turns out somehow my default shell had gotten changed from Bash to SH. Changing my user entry in /etc/passwd from /bin/sh to /bin/bash fixed it.

I should've realized what happened when my shell prompt changed, but then I don't spend that much time in terminals.

--Nathanael

---

### Post by dunbrokin on 2011-09-08
Hmm, that did not work for me...

My terminal suddenly stopped giving me the user name:~$...all it gives is $ and up arrow gives me [[A^ as above....

Have I done something stupid or is my machine compromised?

---

