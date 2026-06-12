---
title: "broken packages"
date: 2006-08-31
forum: Desktop Environments
---

### Post by bwald on 2006-08-31
I recently tried to add the normal debian testing deb packages to my synaptic, and now it says that libc6 and libc6-i686 are broken.  Since these are the GNU C library, I think its pretty important.  When I try to "fix all broken packages" I get this error:

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I'm not sure what to do.

---

### Post by hw-tph on 2006-08-31
Remove the Debian repositories from your sources.list, and run **sudo apt-get update**.


Håkan

---

### Post by bwald on 2006-08-31
Thanks, but I'm still getting the same error.  I deleted the debian testing from the sources.list and from the synaptic gui.  I'm still getting the same error.  I don't know if this helps, but after I try to "fix broken packages" openoffice.org-|10n-en-gb, openoffice.org-|10n-en-us, and openoffice.org-|10n-en-za appear in the "broken" filter of synaptic as well.

---

