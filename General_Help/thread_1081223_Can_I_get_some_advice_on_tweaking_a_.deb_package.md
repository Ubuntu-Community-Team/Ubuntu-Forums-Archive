---
title: "Can I get some advice on tweaking a .deb package?"
date: 2009-02-26
forum: General Help
---

### Post by djbloc on 2009-02-26
I’ve made a few tweaks to customise an original ubuntu supplied .deb package. I would like to now repackage it up so I could distribute it to others.

Two ways I’m considering on how to do this are:

1. Keep the same package name and add a suffix to the version number (similar to what ubuntu does to debian pull-through and adapted packages)

2. Create a completely new package with a new name and add the “Conflicts:” and “Replaces” tags in the control file pointing to the original ubuntu supplied package.

As a result, assuming someone has set up to automatically update their ubuntu distribution, I do not want a newer version of the ubuntu supplied .deb package to override my tweaked one. Which method would you suggest that would do this?

Thanks in advance

---

