---
title: "Ubuntu equivalent of &quot;Default User&quot;"
date: 2008-12-19
forum: Desktop Environments
---

### Post by jcagle on 2008-12-19
Hello all!

I am setting up a Lab of 20 Ubuntu 8.10 machines, they are joined to AD using likewise.

I am trying to create a "Default Profile" of sorts so that anyone who logs in from here on out, will have our standard desktop with all the shortcuts and such.

Google search proved fruitless.

---

### Post by bluefrog on 2008-12-19
customize /etc/skel/ the way you want. Any new user will inherit what's in that folder.

if you have no idea of how to achieve that use sabayon.

---

