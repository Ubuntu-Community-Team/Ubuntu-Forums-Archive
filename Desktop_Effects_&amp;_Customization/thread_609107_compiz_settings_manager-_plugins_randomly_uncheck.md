---
title: "compiz settings manager- plugins randomly uncheck?"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by evan.rotert on 2007-11-10
I am using Kubuntu 7.10 with an NVIDIA GeForce FX 5500, and I have a problem that I thought was isolated to myself but a friend of mine has recently experienced it as well.  I go into the Advanced Desktop Settings Manager and configure my compiz plugins the way I want them.  Things will work fine for a while, but once I've restarted X or rebooted (whether it's once, or after several times) I will suddenly lose some functionality- going back into the settings manager I find that some of my plugins are unchecked!  Generally for me it's "Move Windows" or "Resize Windows" but my friend has had "Desktop Cube," "Rotate Cube" and/or "Wobbly Windows" become unchecked spontaneously as well.  Any thoughts on this?

~Evan

---

### Post by Zorael on 2007-11-10
Try switching to a Flat-file Configuration Backend in Preferences in the settings manager.

Export your profile first, then switch, then import it again to keep your settings.

You may want to add **ccp** as an argument when you start compiz (if you do it through a launcher/script) to make it use its own file format.

---

### Post by evan.rotert on 2007-12-07
Thank you!  If it happens again I'll try it this way :-)

---

