---
title: "Troubleshooting Compiz / Unity Problem"
date: 2013-01-28
forum: Desktop Environments
---

### Post by trundlenut on 2013-01-28
I have an issue with X freezing in 64 bit 12.04.  When I switch to 2D Unity everything is fine so I suspect the issue lies with Compiz, but the various log file yield nothing helpful.  I want to try and troubleshoot/debug compiz but I can't find a way to in 12.04.

I found some information relating to gdb but the compiz packages with the debugging symbols all seem to have been removed in 12.04 and so I'm not sure where to start trying to tackle this.

I can switch to a virtual terminal (ctrl-alt-f1) and restart lightdm or use crtl-alt-backspace and then log back in but the problem reoccurs.  2D Unity is completely fine though.

---

### Post by trundlenut on 2013-02-04
Quick bump.

---

### Post by Pandanus on 2013-02-18
Hello trundlenut,

I don't know what kind of graphics card you are using, but if it is a nvidia you might want to check this bug here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1027211](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1027211)

Good Luck
Pandanus

---

### Post by trundlenut on 2013-02-18
Thanks for that but I have an ATI card.  Also my problem is with X suddenly locking up without warning, up until the point is freezes it runs fine.

---

