---
title: "Kat"
date: 2005-07-29
forum: Desktop Environments
---

### Post by alec on 2005-07-29
Hi,

I have tried to install the KAT .deb found on the KDE apps site, with no luck. Seems to be a problem with the binary - broken pipe!

Does anyone have any info on a working kubuntu binary for this application?

If yes, is it worth installing or should I be looking at Beagle?

---

### Post by SGC on 2005-07-29
Add this repository to /etc/apt/sources.list
```

deb http://dinton.no-ip.org/ kubuntu main
deb-src http://dinton.no-ip.org/ kubuntu main

```

Then:
```

sudo apt-get update
sudo apt-get install kat

```

---

### Post by alec on 2005-07-30
Many thanks,

Worked like a dream. If this is your repository keep up the good work.

Thanks again.

---

### Post by SGC on 2005-07-30
[QUOTE=alec]Many thanks,

Worked like a dream. If this is your repository keep up the good work.

Thanks again.[/QUOTE]
 Its not mine, its Kubuntu-specific repository maintained by Altmenorg, have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=49133](http://ubuntuforums.org/showthread.php?t=49133)

---

