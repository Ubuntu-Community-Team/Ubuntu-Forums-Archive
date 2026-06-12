---
title: "Removing recommended packages from command line in Xubuntu?"
date: 2014-06-24
forum: Desktop Environments
---

### Post by treehuggerguy on 2014-06-24
I made the mistake of installing the Xubuntu-desktop package without the --no-install-recommends option. Does anyone know if there is an easy command line option for removing the recommended packages now that they are installed?

Thanks!

---

### Post by ian-weisser on 2014-06-24
Easy? Yes: Uninstall xubuntu-desktop, and autoremove all the dependencies. Then install xubuntu-desktop again the way you want.

It's easy, but it won't be fast...and it may have unanticipated consequences. It may uninstall packages you want to keep.

---

### Post by treehuggerguy on 2014-06-25
Thanks - I suppose that I may as well try this and just reinstall if there's an issue. I'll try this and see what happens.

> **ian-weisser said:**
> It may uninstall packages you want to keep.

---

