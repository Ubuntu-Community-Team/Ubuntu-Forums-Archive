---
title: "Removed Compiz, reinstalled drivers, and now windows are slow"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by tnunamak on 2008-03-30
Compiz-fusion was causing a few problems and since I plan on doing a clean install when 8.04 is officially released, I uninstalled it. I was having problems with video playback, so I uninstalled the drivers from the restricted-manager, and installed the ones on ATI's website. This didn't work so well, so I reinstalled the restricted drivers. Video playback is fine now, better than it was originally, but when I open firefox, for example, it takes 5-10 seconds for the window to appear and for everything in it to load. As a consequence, everything's slow.

Where should I start?

---

### Post by beren.olvar on 2008-03-30
I had a problem very similar, 
but not only FF was slow, terminals and everything was so slow i couldn't work in the computer..
I couldn't fix that, no matter how many times i reinstalled the drivers, 
so i had to remove xserver-xgl
```
sudo apt-get remove xserver-xgl
```
and reconfigure xserver-xorg with "ati" drivers
```
sudo dpkg-reconfigure xserver-xorg
```

(note that just reconfiguring to use ati instead of fglrx drivers dind't solve the problem,
maybe the issue is with xgl????)
of course you will lose your desktop effects, but
It could be your momentaneus solution, until someone can tell us what to do...
or the release of 8.04

cheers

---

### Post by tnunamak on 2008-04-01
I couldn't take it... I had too much work to do and it was way too slow to be productive, so I did a fresh install. It's amazing how fast that is, by the way, if you put your home directory on a separate partition. I'd highly recommend doing so.

---

