---
title: "Yet another DVD/Kaffiene issue"
date: 2005-08-23
forum: Desktop Environments
---

### Post by PokerFacePenguin on 2005-08-23
I guess I am making this more complex than it should be...playing a DVD shouldn't be this difficult....

Scenario:

I popped in my DVD version of Old School....icon pops up on desktop, but it will not play in kaffiene.

Ok, time to get libdvdcss2  I say...
I head over to [http://lists.ubuntu.com/archives/ubuntu-users/2005-August/045863.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-August/045863.html)

and get the libdvdcss2 .deb file and put it in a local directory on my HD

I follow the instructions listed at that URL (on installing a local .deb) and then enabling DMA (possibly my issue) by issuing the following commands:

```
sudo hdparm -d 1 /dev/dvd
sudo hdparm -c 1 /dev/dvd
``` 

I install libdvdnav4 and libdvdread3 as well after my issue

My Issue:

Now when I pop the OLD SCHOOL dvd in the drive it doesnt pop up the icon on the desktop anymore (but it will pop up a homemade dvd I burned from windows before the conversion).


Kaffiene reports the following (apparently because it cannot find the DVD)

> The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (/dev/dvd) 

and then also

> No plugin found to handle this resource (dvd:/)

Details:
xine: cannot find input plugin for MRL [dvd:/]
xine: input plugin cannot open MRL [dvd:/]
xine: found input plugin : DVD Navigator
xine: cannot find input plugin for MRL []
xine: cannot find input plugin for MRL [dvd:/]
xine: input plugin cannot open MRL [dvd:/]
xine: found input plugin : DVD Navigator
 

Any ideas?

---

