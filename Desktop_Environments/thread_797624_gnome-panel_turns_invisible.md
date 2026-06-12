---
title: "gnome-panel turns invisible"
date: 2008-05-17
forum: Desktop Environments
---

### Post by Locutus_of_Borg on 2008-05-17
On Ubuntu 7.10.  After logging in, the panel appears, then the screen flashes and the icons appear, but the panel never comes back.  It is still there, but completely transparent.  Changing its properties does nothing.  A 'dpkg-reconfigure gnome-panel' was able to fix it once, but now that also does nothing.

Compiz is running on an nvidia card if that makes any difference.

Also, if I create a new panel, that one is also invisible.  I can still click on anything in the panel, just cannot see anything on it.


Any idea as to what this could be?

It didn't always do this, and nothing really has been changed that I can imagine would affect it.  This is not my computer, but I am the one who 'maintains' it, so to speak.

Thanks.

---

### Post by NightwishFan on 2008-05-17
Not sure perhaps it is set to have an opacity of zero with compiz but I doubt it. Move mouse over it, hold in alt and move the mouse wheel up and see if it appears. If not press alt+f2 and try:
```
killall gnome-panel && gnome-panel
```

---

### Post by Locutus_of_Borg on 2008-05-17
no settings in compiz for gnome-panel, though i didnt try to manually raise the opacity

killall and restart brought back a fully transparent panel when i tried it.

the computer in question is now on Vista (i know, i know, but  its owner needed to see the panel for something and i am not exactly sure how to fix it just yet)

but any other suggestions will be very appreciated

---

### Post by kshane on 2008-05-17
> **Locutus_of_Borg said:**
> no settings in compiz for gnome-panel, though i didnt try to manually raise the opacity

killall and restart brought back a fully transparent panel when i tried it.

the computer in question is now on Vista (i know, i know, but  its owner needed to see the panel for something and i am not exactly sure how to fix it just yet)

but any other suggestions will be very appreciated

Try using a background image, for now???

Kevin

---

### Post by Locutus_of_Borg on 2008-05-17
I believe I did try that yesterday, before running the dpkg-reconfigure.

thanks though

---

