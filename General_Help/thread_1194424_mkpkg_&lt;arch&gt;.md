---
title: "mkpkg &lt;arch&gt;"
date: 2009-06-22
forum: General Help
---

### Post by The Switch Blade on 2009-06-22
What do I put?

mkpkg linux?

---

### Post by The Switch Blade on 2009-06-22
> linux:                                  # install Slackwkare Linux binaries
    $ifnfile (bin.linux)
        !mkdir bin.linux
    $endif
        $verbose off
        $set DIRS = "lib src"
        !$(hlib)/mkfloat.csh linux -d $(DIRS)
        ;.

---

