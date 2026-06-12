---
title: "Can we install CPAN Modules using apt-get in ubuntu 6.10"
date: 2007-12-11
forum: Desktop Environments
---

### Post by perljohn on 2007-12-11
Dear All, 


Can we install CPAN Modules using apt-get in ubuntu 6.10 

I am installing All the application using APT-GET .. and i am using APTonCD.

Can we install CAPN Module using APT-GET ??/


Regards
Varghese
Kerala

---

### Post by HankB on 2007-12-11
I'm not aware of a direct way to install modules from CPAN using APT. But I do know that some modules have .deb packages, so you install the .deb and that keeps you within the package management system. Some times the trick is to determine which module is in which deb.

Just last night I installed MP3::Tag; by apt-getting libmp3-tag-perl on my 6.06 LTS box.

HTH,
hank

---

