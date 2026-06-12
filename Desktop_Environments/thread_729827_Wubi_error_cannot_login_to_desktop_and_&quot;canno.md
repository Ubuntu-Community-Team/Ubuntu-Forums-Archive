---
title: "Wubi error: cannot login to desktop and &quot;cannot set mode 0700&quot;"
date: 2008-03-20
forum: Desktop Environments
---

### Post by corvettecraz92 on 2008-03-20
Okay...I had wubi installed perfectly, everything was working. the only problem was, I didn't have enough space. So, i uninstalled, and reinstalled with the 7 gb option in wubi 8.04 (the latest.) Now, I can't even login to the desktop. It says "Your session If you have not logged yourself out, either you have run out of space or there is a problem with the installation." When I click the view details, it gives me a "cannot set mode 0700: *<file in directory>* permission denied"
What do I do?

and BTW, recently it was giving me a $home.dmrc permission error, so I looked it up and changed it with ```
sudo chown <username> ~/.dmrc
chmod 644 ~/.dmrc
```
and it stopped giving me the $home error.

::edit::

okay, maybe i _wasn't_ using the latest installer...I uninstalled and I'm re-installing kubuntu 8.04 with KDE 4...

---

