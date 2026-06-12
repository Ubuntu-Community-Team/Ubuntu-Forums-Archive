---
title: "Firefox 5"
date: 2011-08-08
forum: Desktop Environments
---

### Post by r.darwish on 2011-08-08
I want to use the latest version of Firefox, which is not available in the official repositories. I downloaded the compiled binaries from Firefox website and extracted them to a folder.
When I tried to run firefox-bin it complained about missing shared libraries, which were actually bundled in the same directory with Firefox 5. I set LD_LIBRARY_PATH to the directory where I extracted Firefox 5, then tried to run again. Firefox launched, but it seems that although I run the binary from Firefox 5 directory (I run ./firefox-bin and not just firefox-bin. I also tried an absolute path) the old version of Firefox, which is installed in my system, is always launching instead of the new version. This is pretty confusing.

---

### Post by katherineeobryan on 2011-08-08
The Firefox is the great browser with the compatibility  of all that features e.g java, script, and flash.

---

### Post by mikewhatever on 2011-08-08
Try running firefox instead of firefox-bin.

---

### Post by sikander3786 on 2011-08-08
Why not install it from a PPA? It is the recommended method for the sake of automatic updates.

[http://ubuntu4beginners.blogspot.com/2011/06/firefox-5-stable-arrives-in-official.html](http://ubuntu4beginners.blogspot.com/2011/06/firefox-5-stable-arrives-in-official.html)

---

### Post by lovinglinux on 2011-08-08
Run./firefox instead of ./firefox-bin

See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247") for ppa installation.

---

### Post by r.darwish on 2011-08-08
> **lovinglinux said:**
> Run./firefox instead of ./firefox-bin

See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247") for ppa installation.

Running ./firefox caused the same thing, but updating from the PPA worked. Thank you :)

---

