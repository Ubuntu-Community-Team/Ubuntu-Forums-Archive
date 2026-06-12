---
title: "msttcorefonts"
date: 2005-12-01
forum: Desktop Environments
---

### Post by seismicmike on 2005-12-01
Apt-Get can't find it

When I install from synaptic, I get:

[code]E: msttcorefonts: subprocess post-installation script returned error exit status 1[/conde]

help ](*,)

---

### Post by GeneralZod on 2005-12-01
Try:

```

sudo apt-get install msttcorefonts

```

from a terminal and see what exact errors it spews out.  msttcorefonts needs to download a whole bunch of extra files from a web-site, and I'm betting that that site is having difficulties at the moment (this has happened to me before).

---

### Post by seismicmike on 2005-12-01
I'll just wait it out then, thanks :)

---

