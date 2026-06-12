---
title: "Shell Scripts in Gnome"
date: 2006-10-13
forum: Desktop Environments
---

### Post by thrillhouse on 2006-10-13
Any way to get Ubuntu to stop asking me if I want to "Run in Terminal", "Display", "Cancel", or "Run" a shell script when I double click on it in Gnome?  I want it to run in the terminal all the time.  I have tried associating the script with gnome-terminal, terminal, and sh and it still keeps asking me.  Any thoughts?

---

### Post by kidders on 2006-10-13
Hi there,

I'm not a Gnome expert, but if it were me, I wouldn't try too hard to suppress this message ... even though I'm sure it's *extremely* annoying! Bear in mind that, when running a shell script, a single carelessly-written command can do *serious* damage to your system.

Think of the "Run/Display/Cancel" prompt in terms of what many web browsers do when you try to download something potentially nasty. If you suppressed such warnings, you wouldn't necessarily notice unintended (or unsolicited) downloads, that might be dangerous. Similarly, the Gnome devs probably didn't think it wise to allow shell scripts to execute completely silently.

999 times out of 1000 this message will frustrate the hell out of you ... but you never know when you'll suddenly thank god (Gnome devs = god?!) for the chance to hit "Cancel".

---

### Post by aysiu on 2006-10-13
I agree with kidders. Leave it as is.

But the ability *is* there if you go to Edit > Preferences > Behavior > Executable Text Files in Nautilus.

---

