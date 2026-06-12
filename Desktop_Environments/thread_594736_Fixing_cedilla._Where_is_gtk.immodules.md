---
title: "Fixing cedilla. Where is gtk.immodules?"
date: 2007-10-28
forum: Desktop Environments
---

### Post by daniel_victoria on 2007-10-28
I've always had a problem with Ubuntu and the "&#263;" and "ç" characters. Normaly, using dead-keys, apostrophe plus c (' + c) should give cedilla (ç) but Ubuntu gives accented c (&#263;).

I always fixed this by editing /etc/gtk-2.0/gtk.immodules, adding a en at the end of the cedilla line. From then on, ' + c = ç.
But after my upgrade to Gusty, I can't find the gtk.immodules file. What has happened to it? Any suggestions?

---

### Post by daniel_victoria on 2007-10-28
Found it. The file changed name and place... It's now

/usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules

For the record, adding en at the end of cedilla line will make the ' + c = ç!!!

---

