---
title: "Can't log into a gnome session any more"
date: 2007-04-04
forum: Desktop Environments
---

### Post by DJMatty on 2007-04-04
Hi

I have just done a couple of things to my install and now when I try to log in, it gets some way to showing my desktop and then has a number of errors about panels already running (can't see the exact errors as it all happens a little too fast) and then boots me back to the login prompt again.

I saw some errors to do with panels already running and another to do with nautilus and something about bonobo.

I had just added medibuntu repositories and run the update in synaptic, and when i rebooted this happened.

I am not sure if it was because of the updates for feisty, or because of me using medibuntu, but now i can't do anything else.

I have done some searching and tried deleting the .gnome and .gnome2 folders and the .gconf, and I have also apt-get removed gnome-panel and reinstalled, but none of this has made any difference.

Can someone help me get my desktop back please?

Thanks

Matt

---

### Post by phidia on 2007-04-04
In the CLI you can do > sudo /etc/init.d/gdm start
That should give you the error messages or check /var/log/

---

### Post by DJMatty on 2007-04-05
Hi

I checked the :0.log file in /var/logs/gdm and it said stuff about not being able to start glx.

I manually installed the nvidia drivers and everything is back to normal again!

Thanks

Matt

---

