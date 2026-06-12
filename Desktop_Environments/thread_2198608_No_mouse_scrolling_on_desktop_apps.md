---
title: "No mouse scrolling on desktop apps"
date: 2014-01-09
forum: Desktop Environments
---

### Post by g.wiebe84 on 2014-01-09
I'm running a new install of Ubuntu 13.10 on an Asus M50V. I have a Logitech USB mouse. My issue is that the mouse wheel scrolling does not work on several desktop applications. It works in the terminal but not in "files" program. The mouse scrolling works within the LibreOffice suite but not in the Software Centre. I haven't been able to find any info on this anywhere. 

Your thoughts on this would be greatly appreciated.

---

### Post by mc4man on 2014-01-10
It's quite likely that you're affected by this bug  
[https://bugs.launchpad.net/compiz/+bug/1200829](https://bugs.launchpad.net/compiz/+bug/1200829)
If so then your choices are to stop using 'Viewport-based Desktop scrolling' or make use of a ppa I've setup to workaround till fixed
(probably never in 13.10, for 14.10 it's 50-50
[https://launchpad.net/~mc3man/+archive/test-scroll](https://launchpad.net/~mc3man/+archive/test-scroll)

For 13.10 gtk has been 'fixed' by reverting offending commit, for 14.04 gtk has been been fixed upstream  but also requires a patched xorg

---

### Post by g.wiebe84 on 2014-01-13
> **mc4man said:**
> It's quite likely that you're affected by this bug  
[https://bugs.launchpad.net/compiz/+bug/1200829](https://bugs.launchpad.net/compiz/+bug/1200829)
If so then your choices are to stop using 'Viewport-based Desktop scrolling' or make use of a ppa I've setup to workaround till fixed
(probably never in 13.10, for 14.10 it's 50-50
[https://launchpad.net/~mc3man/+archive/test-scroll](https://launchpad.net/~mc3man/+archive/test-scroll)

For 13.10 gtk has been 'fixed' by reverting offending commit, for 14.04 gtk has been been fixed upstream  but also requires a patched xorg

@ mc4man, thanks for the info. Currently, I can work with this foolishness. I don't know if this is another attempt by the Ubuntu dev team to relegate Compiz to the dust bin or not. This would have been quite apparent during development had Compiz been utilized.

---

