---
title: "GnuCash Again"
date: 2005-12-31
forum: General Help
---

### Post by John Jason Jordan on 2005-12-31
Back when I had 64-bit Hoary I used GnuCash and it was fine. However, it broke after upgrading to 64-bit Breezy. I had to uninstall it due to library conflicts. Thinking the problem might be fixed by now I just installed it again. Installation went OK except Synaptic popped up a message about needing to overwrite a file. I clicked on OK and it proceeded normally.

However, it did not install a launch shortcut in Applications on my panel. I decided to launch it from the command line for the time being (I can fix the panel later). When I typed "gnucash" it popped up the splash screen for a moment, which then disappeared. A few moments later the terminal window said "gnucash: [W] "failure loading "#f."

Being pretty new to Linux I have no idea what that means, except that it is probably something still related to the library issue. But this is a different error than I had before. As I recall the previous problem occurred with both 32-bit and 64-bit Breezy (but I might have misremembered that). Does anyone know how to get it to run on Breezy?

---

### Post by John Jason Jordan on 2006-01-01
I finally solved the problem and got GnuCash working on 64-bit Breezy.

1) Launch Synaptic and uninstall it.
2) Scroll down the list of applications in Synaptic and note that libofc-forget-the-rest-of-the-name is no longer listed. Evidently this was a bogus package that GnuCash installed, and uninstalling GnuCash removed it.
3 (the important part) Install libofx2. Do this before installing GnuCash
4) When libofx2 has been installed, then install GnuCash.

Being a beginner at Linux, I have no idea why this worked, but at least one more of my problems has been resolved.

---

