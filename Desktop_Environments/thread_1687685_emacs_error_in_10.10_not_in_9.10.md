---
title: "emacs error in 10.10 not in 9.10"
date: 2011-02-14
forum: Desktop Environments
---

### Post by Skaperen on 2011-02-14
I'm getting the following error message from emacs when editing a .c file under 10.10 that I do not get under 9.10:```
File mode specification error: (void-function c-setup-paragraph-variables)
```It appears to be the same version of emacs itself (22.2.1), but a revision of the Ubuntu packaging:

On 10.10 (dpkg formats wider than on 9.10):```
ii  emacs22                               22.2-0ubuntu9                                     The GNU Emacs editor (Emacs 22)
ii  emacs22-bin-common                    22.2-0ubuntu9                                     The GNU Emacs editor's shared, architecture dependent files
ii  emacs22-common                        22.2-0ubuntu9                                     The GNU Emacs editor's common infrastructure
ii  emacs22-el                            22.2-0ubuntu9                                     GNU Emacs LISP (.el) files
**ii  emacs22-gtk                           22.2-0ubuntu9                                     The GNU Emacs editor (with GTK+ **2.x support)
ii  emacs22-nox                           22.2-0ubuntu9                                     The GNU Emacs editor (without X support)
ii  emacsen-common                        1.4.19ubuntu1                                     Common facilities for all emacsen
```On 9.10:```
ii  emacs22                           22.2-0ubuntu6.2                   The GNU Emacs editor (Emacs 22)
ii  emacs22-bin-common                22.2-0ubuntu6.2                   The GNU Emacs editor's shared, architecture 
ii  emacs22-common                    22.2-0ubuntu6.2                   The GNU Emacs editor's common infrastructure
ii  emacs22-el                        22.2-0ubuntu6.2                   GNU Emacs LISP (.el) files
ii  emacs22-nox                       22.2-0ubuntu6.2                   The GNU Emacs editor (without X support)
ii  emacsen-common                    1.4.19ubuntu1                     Common facilities for all emacsen
```Could this be due to the fact that 10.10 has a "-gtk" package, or due to the package version 6.2 -> 9 ??

---

### Post by Skaperen on 2011-02-24
*_z_*

---

