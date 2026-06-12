---
title: "Enable Hardware Acceleration ?"
date: 2006-05-21
forum: Desktop Environments
---

### Post by i++ on 2006-05-21
i want to get 3ddesk running, but when i try and run it i get the following error...

```
$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)
```

any idea's how to enable/configure hardware acceleration? i am running breezy 5.10 with radeon x800 with the radeon, rather than ati, driver.

thanks! :)

---

### Post by Fass on 2006-05-21
Get the fglrx driver. Ati and Radeon won't cut it.

---

### Post by i++ on 2006-05-21
okay, sorry to be a n00b :$ but how do i get that? can i just edit xorg.conf?

---

### Post by Ramses de Norre on 2006-05-21
```
sudo aptitude install xorg-driver-fglrx
```
Then set driver in xorg.conf to fglrx.

---

### Post by i++ on 2006-05-21
thanks that worked well! althought my ubuntu runs very sluggishly with fglrx as driver... any idea why?

---

### Post by Wormsie on 2006-05-27
Sorry for posting, now I think I know what is wrong...

---

