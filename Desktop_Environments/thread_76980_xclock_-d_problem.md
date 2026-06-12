---
title: "xclock -d problem"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Tralobyte on 2005-10-16
The command "xclock -d" does not work correctly. It's just displaying "20" instead of the time.

EDIT: I solved the problem by getting the latest source code from x.org (version 6.8.2,) building it, and copying the file .../xc/programs/xclock/xclock to /usr/bin/. If you do this, make sure to back up the xclock installed with Breezy from /usr/bin/xclock to something like /usr/bin/xclock.bak.

Any better methods are welcome.

---

