---
title: "Slow Gedit with different icon sets"
date: 2008-11-04
forum: Desktop Environments
---

### Post by Yashiro on 2008-11-04
Just posting to make people aware that loading alternate icon sets can have a large impact on your some applications performance.

Icon sets that are significantly larger (data wise)than the base gnome/human set can slow apps to a crawl.

For example, Gedit. **Using an icon set that is larger (data wise) than the default makes this app load very slowly. **

Whether this manifests particularly badly in this case it's hard to say. But gedit startup is severely hampered by a 'better' set of icons. It could be just a gedit issue as a strace does show it enumerating every available icon available before it finishes loading.

Just something I noticed today while playing with icon themes. :popcorn:

---

### Post by robertyou on 2008-11-17
> **NilsE said:**
> While waiting for the bug fix in the meantime you can go into 

Edit >Preferences > Plugins 

and turn off the File Browser pane.

The slow start-up of gedit is actually a bug of it's plugin "File Browser pane. Just un-check it to retain the speed. :)

---

### Post by Yashiro on 2009-01-29
There is that bug, yes, but the issue in my post also exists.

---

### Post by Flos Headford on 2010-03-22
Thanks to robertyou!
that tip is still needed, two years after you posted....
Verb sap.
Phil

---

