---
title: "USB ext keyboard: alphanumeric keystrokes not recognised"
date: 2013-03-12
forum: Desktop Environments
---

### Post by henrylaw on 2013-03-12
Bizarre condition on my newly-installed 12.04 system, running 32-bit on oldish hardware.  Worked fine until yesterday; now when I log in regular keystrokes (alphanumeric, for example) are not recognised by any application running under Unity: Terminal and Firefox for example.  The "super" key is recognised and brings up the dash, but I can't then type into the search box.  If I open Terminal using the mouse then I can't type into it, but each keypress makes the cursor flash, as if some kind of interrupt were being recognised.

I can open a TTY session using Crtl/Alt/F1; the keyboard then works fine; but when I come back to Unity via Ctrl/Alt/F7 the not-listening-to-you condition remains.

What have I done since it last worked?  Removed (what I thought were) all the Libreoffice packages; I did this programatically using ```
sudo apt-get remove `dpkg -l | grep libreoffice | awk '{print $2}' | tr "\\n" " "`
``` but that means I can't immediately look in history to see which packages I removed.  

Any suggestions?  If it's a package that I've mistakenly removed, do you know which one?

---

