---
title: "Broken LIRC irsend"
date: 2006-06-22
forum: Desktop Environments
---

### Post by superm1 on 2006-06-22
As some people here have already determined I'm sure, lirc is quite broken in dapper.  The package that is available won't build modules against the current dapper kernel.

I opted to grab the debian unstable package instead and use that.  Now this works fine for receiving from two transmitters that I have (mceusb and mceusb2 based).  Now, I have an amd64 machine running gentoo with a proven working configuration for lirc with irsend and receive. I installed dapper on another partition, copied over the remote file and spawned it the same way as on the gentoo machine, and ir transmitting doesn't work.  I tried on two other x86 dapper machines with the same trouble.  This same transmitter works on winLirc too.

I filed a bug with debian, but haven't seen too much response about it, so I was wondering if the rest of the community has seen any of this.

Debian unstable bug indicating broken IR transmititng: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=373871](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=373871)

Ubuntu Launchpad bug indicating broken lirc modules in dapper: [https://launchpad.net/products/lirc/+bug/45703](https://launchpad.net/products/lirc/+bug/45703)

Now with that all being said, does anyone else have difficulties with lirc and transmitting in dapper?

---

