---
title: "Trying to remove cdcollect to no avail :("
date: 2006-01-04
forum: General Help
---

### Post by kwaanens on 2006-01-04
I recently wanted to try cdcollect and installed it ([http://cdcollect.sourceforge.net/](http://cdcollect.sourceforge.net/)) by the help of a deb I found [here]("http://sourceforge.net/project/showfiles.php?group_id=119228")

I have absolutely no use for it, but can't seem to remove it (loosely translated, as my console is in Norwegian):

```
$ sudo apt-get remove cdcollect
Reading package lists ... Done
Building dependencies ... Done
The following packages will be REMOVED:
  cdcollect
0 upgraded, 0 newly installed, 1 to remove og 0 not upgraded.
Need to get 0B of files.
After... 553kB will be freed.
Would you like to continue [Y/n]? Y
(Leser database ... 145697 filer og kataloger er installerte.)
Removing cdcollect ...
/var/lib/dpkg/info/cdcollect.prerm: line 5: /usr/sbin/gconf-schemas: No such file or directory
dpkg: Feil ved behandling av cdcollect (--remove):
 subprocess pre-removal script returned error code 1
Det oppsto feil ved behandling av:
 cdcollect
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What to do?

- Ketil

---

