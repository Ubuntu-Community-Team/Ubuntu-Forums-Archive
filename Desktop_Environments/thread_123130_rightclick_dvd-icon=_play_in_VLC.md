---
title: "rightclick dvd-icon= play in VLC"
date: 2006-01-29
forum: Desktop Environments
---

### Post by maxdevis on 2006-01-29
how can i make it that when there's a dvd-movie in my dvd-drive, i just have to rights-click on the dvd-icon on my desktop and select "play in vlc". And then it begins?

is that possible?

---

### Post by Perfect Storm on 2006-01-29
For automatically play when DVD inserted for VLC: [http://ubuntuforums.org/showthread.php?t=77146](http://ubuntuforums.org/showthread.php?t=77146)


Allmost as good for what you seek:
Add Disk mounter applet to your panel, you just need to do what's described in the link above to getting it to work properly.
Right click panel ----> Add to panel ----> Disk Mounter.

Now you can click the DVD icons and a menu appers with play or eject.

---

### Post by maxdevis on 2006-01-29
thanks for the reply.
i think i will use it, 
but i'm still looking for a program dat kan change my right-click-menu.

---

### Post by Perfect Storm on 2006-01-29
I'm wonder if a nautilus script can do that....havn't tried....

---

### Post by maxdevis on 2006-01-29
i made my first script!
i don't know it's "kosjer", but it works

#!/bin/bash
#
for I in "$*"
do

wxvlc dvd:///dev/dvd

done
done
exit0

---

### Post by Perfect Storm on 2006-01-29
Grats! :)

---

