---
title: "1420N Vesa only advanced graphics fails"
date: 2007-12-23
forum: Dell  Ubuntu Support
---

### Post by jebblue on 2007-12-23
I upgraded our 1420N using the Ubuntu upgrade utility. I'm not sure what the graphics driver was before but now on 7.10 it is vesa, I've tried using dpkg-reconfigure xserver-xorg but it refuses to use anything but the plain vesa driver.

Any suggestions how to get Gutsy on 1420N to use better video drivers?

---

### Post by jebblue on 2007-12-23
Turns out Dell has a Launchpad bug to track this with some good information:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

---

### Post by sciurus on 2007-12-24
Try the x configuration [here]("http://ubuntuforums.org/showthread.php?t=617934").

---

### Post by jebblue on 2007-12-27
I went back and tried "dpkg-reconfigure xorg-server" and it works, thanks.

---

