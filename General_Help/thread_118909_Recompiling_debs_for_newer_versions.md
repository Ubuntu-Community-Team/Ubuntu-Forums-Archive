---
title: "Recompiling debs for newer versions"
date: 2006-01-18
forum: General Help
---

### Post by exclipy on 2006-01-18
Hi all,

I'm using a little package called bitlbee from the ubuntu/universe repository, but the packaged version is bitlbee-0.92 and since then, bitlbee-1.01 has been released.  To cook a deb of the new version, I'm under the impression that I can just unpack the src.deb, swap in the the new source files and rebuild it?  Can someone please give (or post the URL to) some instructions on exactly how to do this?

Thanks.

---

### Post by psychicdragon on 2006-01-18
An easy way to make a deb file from source is to use checkinstall (it's in universe).

Then instead of the usual ./configure;make;sudo make install, use ./configure; make; sudo checkinstall. It will create a deb file for you and install it.

---

### Post by exclipy on 2006-01-18
Yes, but I want to keep the same settings as the one in the repos so that I can just upgrade cleanly to it.

---

