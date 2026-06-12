---
title: "aDesklets widgets not working"
date: 2010-06-05
forum: Desktop Environments
---

### Post by rewritems on 2010-06-05
Hi, so I installed adesklets, no big deal, and python compiler too. But when I tried to add a widget, I got this:

```

Retrieving data online... OK
Checking locally installed desklets... OK
Downloading acpi_battery desklet... OK
Verifying download integrity... OK
!!! An error occured during the operating !!!
Traceback (most recent last call):
 File "/usr/bin/adesklets_installer", line 223 in run
  getattr(self, '_'+op)(**kw)
 File "usr/bin/adesklets_installer", line 224, in _install
  self.desklets.install(desklet) # refresh of desklets states
 File "/usr/bin/adesklets_installer", line 146, in install
   raise RuntimeError:('bad download checksum')
RuntimeError: bad download checksum


``` don't get it, everything went fine. The installation everything. Perhaps I should manually install the widgets?

EDIT: Okay so I  noticed this when I went in the terminal and typed in "adesklets_installer" to start the adesklets app:

```

/usr/bin/adesklets_installer:44: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import os, os.path, re, tarfile, md5, StringIO, cStringIO, copy, time

```

---

### Post by rewritems on 2010-06-06
Bump. Can someone please help me? That is indeed the full error, rather, report of my error

---

