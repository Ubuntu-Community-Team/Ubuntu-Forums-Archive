---
title: "Bug in locale?"
date: 2005-09-17
forum: Desktop Environments
---

### Post by NiN on 2005-09-17
Hi!

I was trying to get ubuntu working with serbian locales,
but the locale-generation did not work.

The error was this message:

[email]root@paradise-lost:/usr/src/glibc-2.3.2.ds[/email]1 # dpkg-reconfigure locales
Generating locales...
  de_AT.UTF-8... done
  en_US.UTF-8... done
  de_DE.UTF-8... done
  en_GB.UTF-8... done
  sr_YU.UTF-8...LC_ADDRESS: `country_ab2' value does not match `country_num' value
LC_ADDRESS: `country_ab3' value does not match `country_num' value

Already tried google, but no usable search results show up.

Anyone who knows how to get this to work?

EDIT:

Forgotten to say:

Problem exists in Hoary and Breezy Preview

EDIT:

Filed a bug report.
Access now under:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15779](http://bugzilla.ubuntu.com/show_bug.cgi?id=15779)

---

