---
title: "cannot install Firefox"
date: 2010-09-23
forum: Desktop Environments
---

### Post by samaricsm on 2010-09-23
An upgrade for Firefox failed about a month ago, complaining of a broken link.  After this all package updates fail to apply.  I finally was successful in removing Firefox, today.  I had to manually erase it.  The Synaptic Package Manager could not remove it.

When I try to reinstall Firefox I get the message "Error in package ubufox", but the files have been installed and I can actually run the application, however, the Synaptic Package Manager still thinks the package must be reinstalled.  

I have uninstalled and tried the install several times without success.  Always the same error message.  I have tried:
apt-get install -f           {it comes back clean}
apt-get update               {it is happy}
aptitude clean               {it is happy}
dpkg --configure -a          {it comes back clean}
aptitude upgrade             {it comes back clean}

By this time everything seems OK, however, the Firefox install fails with "Error in package ubufox".

Needless to say, this is more than a little frustrating.

---

