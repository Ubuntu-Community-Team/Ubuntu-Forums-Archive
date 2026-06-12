---
title: "Cant log in or ugrade"
date: 2005-04-13
forum: Desktop Environments
---

### Post by robtotheb on 2005-04-13
Have a strange problem with my Ubuntu after updating Hoary afew weeks ago.  When I log in all I get is the brown background and the mouse cursor the only way I can get a working desktop is if I choose gnome in the sessions window but then when I want to log out there is no shutdown/restart option (v annoying).  Also when I try to upgrade/update is synaptic I get this error.

E: /var/cache/apt/archives/xlibmesa-gl_6.8.2-10_i386.deb:  trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package fglrx-6-8-0


What have I done wrong?!

---

### Post by maqi on 2005-04-13
You have installed the ATI drivers from the ATI rpm package rather than the ubuntu package. And you would have had to force the installation. And now xlibmesa-gl is getting upset because it wants to put it's own libGL.so.1.2 (which was forcibly overwritten by the fglrx-6-8-0 install) back. 

Try forcing the install of xlibmesa-gl. You will have to do it from the command line:

```
apt-get install --force-yes xlibmesa-gl
```

and forcibly removing fglrx-6-8-0 from the command line.

I had this problem and this solved it. But I can't remember which order I did it in - but I think apt will only let you do it in one order. Either way, at the end of it you will need to reinstall the ATI drivers. 

EDIT: Come to think of it I think I may have forced the removal of fglrx-6-8-0 first and then I didn't need to force the install of xlibmesa-gl. Wish I'd written it down :(

If you use the ubuntu fglrx packages you won't have this problem in future. 

Hope this helps :)
maqi

P.S. did you draw that Breezy Badger on one of the other forums?

---

### Post by robtotheb on 2005-04-13
When I try to force either removal apt says

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

PS No didnt draw it just saw it and liked it!

IGNORE THAT I still had Synaptic open :P
Working now... thanks alot  \\:D/

---

