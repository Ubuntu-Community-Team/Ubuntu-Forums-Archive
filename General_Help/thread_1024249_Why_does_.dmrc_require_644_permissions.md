---
title: "Why does .dmrc require 644 permissions?"
date: 2008-12-28
forum: General Help
---

### Post by ajcham on 2008-12-28
I, like many others, have previously experienced the following problem:
[INDENT]*User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users.*[/INDENT]

I was able to understand the problem and fix it without issue, however the one thing I am unable to grasp is the reason for the permissions being 644. Why do other users need read access to an individual's .dmrc file? This is especially confusing in light of the fact that the $home directory itself is allowed to have 700 permissions, rendering the file inaccessible to others anyway.

Any ideas?

---

### Post by p_quarles on 2008-12-28
I would hazard that it's because the display manager does not run as your user, but nonetheless needs to be able to read its resource file.

---

### Post by ajcham on 2008-12-30
> **p_quarles said:**
> I would hazard that it's because the display manager does not run as your user, but nonetheless needs to be able to read its resource file.

Makes sense, but wouldn't the 700 permissions on ~/ take precedent over .dmrc's 644 permissions, thereby still preventing access?

:confused:

---

