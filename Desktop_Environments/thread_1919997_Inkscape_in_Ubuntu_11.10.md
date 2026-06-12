---
title: "Inkscape in Ubuntu 11.10"
date: 2012-02-03
forum: Desktop Environments
---

### Post by Acharn on 2012-02-03
I'm having a problem installing Inkscape in Oneiric Ocelot (Ununtu 11.10). In the Ubuntu Software Center I get a message, "Inkscape: Package dependencies cannot be resolved. Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4 dfsg-3ubuntu3 is to be installed." If I try "sudo apt-get install inkscape" in the terminal, I get:
The following packages have unmet dependencies:
 inkscape : Depends: libmagick++3 (>= 7:6.6.2.6) but it is not installable
            Depends: libpoppler-glib5 but it is not installable
            Depends: libpoppler7 but it is not installable
            Depends: libwpd8c2a but it is not installable
            Depends: libwpg-0.1-1 but it is not installable
            Recommends: libwmf-bin but it is not installable
            Recommends: python-numpy but it is not installable
            Recommends: python-lxml but it is not installable
            Recommends: python-uniconvertor but it is not installable
            Recommends: perlmagick

The last line is"
E: Unable to correct problems, you have held broken packages.

Broken packages? What can I do about that? Can anyone tell me how to install Inkscape? I had it on my Windows machines for years. What's going on here? It was a native Linux program ( the GNU Image Manipulation Program ) from the beginning! How can this be?

---

### Post by mikewhatever on 2012-02-03
You seem to have some repository mismatch or mix up. Can you post the output of the following from a terminal window:

```
cat /etc/apt/sources.list
```

---

### Post by Acharn on 2012-02-04
Thanks for the offer of help, but I managed to get it working by following all the steps at [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure) Even after that the Ubuntu Software Center acted funny, but it installed from the terminal without a problem. Glad I don't have to do that very often.

---

