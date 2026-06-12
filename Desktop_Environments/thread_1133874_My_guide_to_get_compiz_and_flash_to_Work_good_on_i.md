---
title: "My guide to get compiz and flash to Work good on intel 965 under Jaunty"
date: 2009-04-23
forum: Desktop Environments
---

### Post by GOROSSI on 2009-04-23
Hi this is how I got Flash and Compiz working under 9.04 Jaunty Jacklope

1: I removed the compiz blacklist  by

sudo gedit /usr/bin/compiz

finding the line 

T="$T 8086:2a02 " # Intel GM965

then disabling it with a #

#T="$T 8086:2a02 " # Intel GM965

then saved and logged out.

2: This part is optional 

As per the release notes I enabled UXA acceleration in .etc/X11/xorg.conf.

see here [http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards") 


Though if you choose to do it don't enable compiz till you have done so

---

