---
title: "Backing store problem"
date: 2008-02-03
forum: Desktop Environments
---

### Post by Mohammed Tarek Elfarargy on 2008-02-03
Hi everybody,
I have a serious problem with the backing store. I'm working on an application that requires the backing store enabled. I tried almost everything I can think about but sadly nothing worked. I modified my xorg.conf and added the :
 Option   "backingstore"	"true"
under various device sections (I don't know which among them exactly is responsible for the change but now I get  :
options:    backing-store YES, save-unders YES
when I enter : "xdpyinfo | grep backing" in terminal ). I also modified the /etc/X11/xinit/xserverrc and added the "-wm" and "+bs" options, so now my file looks like this:

#!/bin/sh
exec /usr/bin/X11/X -dpi 100 -nolisten tcp -wm +bs 

I can't think of anything else to do to enable backing store so any help will be extremely useful .
Thanks for reading this.

---

### Post by rienrien on 2008-02-06
Hi,  I had the same problem. I found the solution [in this forum]("http://forum.compiz-fusion.org/showthread.php?t=6794"): add the following line to /etc/X11/xorg.conf under Section "Device":      

Option "BackingStore" "True"

It used to be possible to turn it on in /etc/gdm/gdm.conf but I couldn't get it to work. Hope this works.

---

### Post by avenca on 2008-05-19
I had the same problem when I was using the "i810" driver. It was solved when I changed the driver to "intel" in the /etc/X11/xorg.conf. Good luck.

---

