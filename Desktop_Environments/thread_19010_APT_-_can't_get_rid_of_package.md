---
title: "APT - can't get rid of package"
date: 2005-03-09
forum: Desktop Environments
---

### Post by unkwn on 2005-03-09
Yesterday i tried to install plone/zope and during the process it buggered up. now it's half installed and i can't even use apt.

Whenever i go to do anything in synaptic it is trying to remove this 'plone-site' package before anything, looks like this:

[PHP](Reading database ... 70205 files and directories currently installed.)
Removing plone-site ...
dzhandle zopectl: unknown instance `plone-site'
dpkg: error processing plone-site (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 plone-site
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/PHP]

Any ideas how i can get rid of this little bugger?

---

### Post by Malifice on 2005-03-10
I had the same problem once, and I get rid of the package using dselect.

---

