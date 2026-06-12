---
title: "Can't Install Updates"
date: 2009-02-06
forum: General Help
---

### Post by ALIENDUDE5300 on 2009-02-06
I've been using Ubuntu for quite some time now, and just recently, I have lost the ability to install updates. Something appears to be wrong with Aptitude's GPG Keys. When I attempt to check for and install updates as root, the following message appears: "W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783". I have tried running Aptitude's clean command, but I am still having problems. :( Help would be appreciated, thanks!

---

### Post by mb_webguy on 2009-02-06
Have you installed the medibuntu-keyring package?  If so, try reinstalling it.

---

### Post by ALIENDUDE5300 on 2009-02-06
Yeah, I have that package installed. After reinstalling it, everything works fine! Thanks for the quick reply! :D

---

