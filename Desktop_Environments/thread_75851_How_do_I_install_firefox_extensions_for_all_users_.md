---
title: "How do I install firefox extensions for all users at the same time?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by joanverde on 2005-10-14
How do I install firefox extensions for all users at the same time?

As for now I 've got to remake the install for every single user, quite annoying.

Regards,
John

---

### Post by iimess on 2005-10-14
[http://www.mozilla.org/projects/firefox/extensions/commandlineoptions.html](http://www.mozilla.org/projects/firefox/extensions/commandlineoptions.html)

-install-global-extension "/path/to/extension"
    Installs the extension into the application directory. The parameter is the path to the extension. Use -lock-item {GUID} afterwards to prevent a single user from disabling or uninstalling the extension globally.

---

### Post by aysiu on 2005-10-14
Are you installing a whole bunch of extensions at once, or one at a time over a long period? If it's a whole bunch of extensions at once, I'd install them all for one user, then copy the /home/username/.mozilla file to all the other users.

---

