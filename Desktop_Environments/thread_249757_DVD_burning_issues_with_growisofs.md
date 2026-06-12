---
title: "DVD burning issues with growisofs"
date: 2006-09-03
forum: Desktop Environments
---

### Post by sdhoigt on 2006-09-03
I consistently have DVD burning issues with Ubuntu 6.06.  Here is the error I get.

$ sudo growisofs -speed=2 -Z /dev/dvd -dvd-video dvd
...
 81.00% done, estimate finish Wed Aug 16 21:36:13 2006
 81.30% done, estimate finish Wed Aug 16 21:36:13 2006
 81.61% done, estimate finish Wed Aug 16 21:36:12 2006
 81.91% done, estimate finish Wed Aug 16 21:36:12 2006
:-? the LUN appears to be stuck writing LBA=14c1d0h, retry in 0ms
:-[ WRITE@LBA=8014c1d0h failed with SK=2h/ASC=04h/ACQ=08h]: Resource temporarily unavailable
builtin_dd: 1360336*2KB out @ average 6.1x1385KBps
:-( write failed: Resource temporarily unavailable


I have a growing coaster collection due to this error.  The percentage finished varies from burn to burn.  I've seen it below 10% and anywhere up to 90+%.  I went through a TDK DVD-R 50 pack on Debian testing w/o any problems.  And I bought a new 50 pack (TDK again) and switched to Ubuntu 6.06 at the same time, so I'm not sure if the problem is media or OS related.  I'm leaning towards OS at the moment.  Once in a while I do get a successful burn, but that happens only about 20% of the time.

I've tried burning from the command line before logging into the desktop thinking there'd be fewer background processes, but that didn't help.

I read in another thread regarding this error that says the DVD drive somehow becomes busy and that's what stops the burn.  I'm not sure what would be doing that.  Maybe the Beagle daemon?

I'm stumped.  Thanks for reading... and any input/experiences would be much obliged.

SD

---

### Post by sdhoigt on 2006-09-29
I think I've got this figured out.  I've had 4-5 successful burns in a row w/o any issues.

I upgraded the version of growisofs (5.something) that comes on Ubuntu 6.06 to growisofs (6.1).

I kinda cheated and just pulled out the binaries for the growiso package from Debian testing.  If you actually install the Debian package, apt-get will fuss and fight to remove it.

So just pull out the binaries and stick them somewhere like /opt/bin or /usr/local/bin

Just as long as they're in your path, everything should work just fine.

SD

---

