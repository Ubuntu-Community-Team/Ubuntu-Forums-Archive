---
title: "Understanding the DISPLAY variable"
date: 2009-03-11
forum: General Help
---

### Post by kevdog on 2009-03-11
I was looking for some reference or background on the DISPLAY variable that is used with the X windowing system.

I know for example if using a ssh forwarding connection, to set the DISPLAY variable to 0.0 (meaning localhost), to have x programs start on the ssh client's machine.  Of course the ssh client's machine would need to running the xserver in the background.

Would there ever be any instance for example where you would set the DISPLAY variable to anything else other than 0.0

Please not the command I am referencing is the following:
export DISPLAY=:0.0

---

### Post by pennacook on 2009-03-11
well, if you want to display a xterm (or whatever) to a different machine and don't tunnel it through ssh, you can set your DISPLAY variable back to the machine you are wanting the xterm to actually show on.

---

### Post by kevdog on 2009-03-11
How do I do this?  What other values are there other than 0.0 and when would these be applicable?

---

