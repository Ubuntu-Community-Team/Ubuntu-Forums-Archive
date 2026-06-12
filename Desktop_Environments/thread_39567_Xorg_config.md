---
title: "Xorg config"
date: 2005-06-05
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-05
Can anyone remind me how to access the xorg config blue-screen GUI that configures your file based on selections? Thanks!

---

### Post by tdell on 2005-06-05
In a terminal type:

dpkg-reconfigure xserver-xorg

Tom

---

### Post by jobezone on 2005-06-05
[QUOTE=Curlydave]Can anyone remind me how to access the xorg config blue-screen GUI that configures your file based on selections? Thanks![/QUOTE]

If you ever forget the exact command, you can allways do it in Synaptic.

In synaptic, search for xserver-xorg . Select the package, and click on the menu Package->Configure .

Many other packages use debconf, Debian's configuration system, but not all. To see which ones do, select the Filters tab in Synaptic. There is one filter called "packages with debconf" or similar.

---

### Post by Curlydave on 2005-06-05
Hey, thanks alot, that was the command! I dind't know you could do it that way in Synaptic, nice.

---

