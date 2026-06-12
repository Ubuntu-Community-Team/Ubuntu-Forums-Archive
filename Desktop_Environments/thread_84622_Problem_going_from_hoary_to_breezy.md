---
title: "Problem going from hoary to breezy"
date: 2005-10-31
forum: Desktop Environments
---

### Post by feamsr00 on 2005-10-31
I was trying to upgrade hoary hedghog to breezy badger ubuntu 5.10, I ran into this problem.  
Unpacking replacement grepmap ...
Preparing to replace gzip 1.3.5-9ubuntu3.4 (using .../gzip_1.3.5-11ubuntu2_i386.deb) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Unpacking replacement gzip ...
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please any information will help.  
Thank you for you time.

---

### Post by dcstar on 2005-10-31
[QUOTE=feamsr00]I was trying to upgrade hoary hedghog to breezy badger ubuntu 5.10, I ran into this problem.  
Unpacking replacement grepmap ...
Preparing to replace gzip 1.3.5-9ubuntu3.4 (using .../gzip_1.3.5-11ubuntu2_i386.deb) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Unpacking replacement gzip ...
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please any information will help.  
Thank you for you time.[/QUOTE]

I had the Locale message on my upgrade (all over the place, slightly different as I had the "en_AU" locale in my system), but it didn't seem to affect my upgrade.

Do you have enough disk space on you system?

---

