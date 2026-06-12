---
title: "compiz solution ?"
date: 2010-05-23
forum: Desktop Environments
---

### Post by Hagar55 on 2010-05-23
I've been looking for a long time for my problems with compiz...no one seems to have the answer to this problem:

Distribution: Ubuntu 10.04
Desktop environment: GNOME
Graphics chip: ATI Technologies Inc Mobility Radeon HD 3650
Driver in use: fglrx
Rendering method: None

Checking if it's possible to run Compiz on your system... [SKIP]

Checking for hardware/setup problems... [SKIP]

At least one check had to be skipped:
Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

now I found a possible solution somewhere, do any of you know if this is trustworhty to try or likely to help ?
As this was a soltion for Karmic and I'm using Lucid.

[http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/](http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/)

---

### Post by wojox on 2010-05-24
It should. There's a repo for lucid in there [https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill)

---

### Post by Hagar55 on 2010-05-24
And yes it worked like a charm...
Will it keep using the patched version or will it do the way of the dodo when a new version of x-org comes out ?

---

