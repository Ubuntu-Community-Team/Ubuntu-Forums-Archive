---
title: "Nautilus menubar behind panel"
date: 2011-10-24
forum: Desktop Environments
---

### Post by Arachan on 2011-10-24
Hello,

I recently installed Ubuntu 11.10 and added XCFE. I'm enjoying it a lot, but one bug is still annoying me. 'Behind' my panel appears to be a nautilus menu bar, the same as how it is if you have nautilus open in regular Ubuntu. It doesn't seem to be functional, but it does ruin the transparency effect of my panel. If I kill nautilus it goes away, so it definitely is part of nautilus.

Here is a screenshot of what I mean. 

[IMG]http://ubuntuforums.org/picture.php?albumid=2237&pictureid=8238[/IMG]

I'm assuming this is caused by some vestigial trace of unity or something?

Anyone know how to get rid of this? 

Also, on a side note, I can't seem to stop auto-login. Anyone know how in xubuntu?

Thanks,
arachan.

---

### Post by crdlb on 2011-10-25
Uninstall appmenu-gtk3 and restart nautilus.

---

### Post by Arachan on 2011-10-25
> **crdlb said:**
> Uninstall appmenu-gtk3 and restart nautilus.

Hello,

I tried your suggestion and it's still there. Do I need to restart the session or computer for it to take affect?

Thanks for your help,
arachan.

---

### Post by crdlb on 2011-10-25
Restarting nautilus (nautilus -q or killall nautilus) should be enough. You could try logging out if that doesn't work.

---

### Post by Arachan on 2011-10-25
> **crdlb said:**
> Restarting nautilus (nautilus -q or killall nautilus) should be enough. You could try logging out if that doesn't work.

Hello,

I logged out and back in again and it's gone.  It even fixed another random bug I had, so that's fantastic.

Thanks a lot mate :)
arachan.

---

