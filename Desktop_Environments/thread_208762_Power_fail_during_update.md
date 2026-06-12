---
title: "Power fail during update"
date: 2006-07-04
forum: Desktop Environments
---

### Post by RoyB (Aus) on 2006-07-04
Successfully installed desktop.  Then began 91 mb update of various packages.

After all the downloads had finished and while they were installing I had a power failure.

Re-booted ok after power came up, but now when I try to use the update tool I get an error messages that says 

"Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'synaptic' first.

What to do to recover?

---

### Post by RoyB (Aus) on 2006-07-04
I think I found the solution:

dpkg --configure -a
   and
sudo apt-get install -f

Seems to have fixed everything

---

