---
title: "Hwo to compress .xpi_FILES folder to .xpi ?"
date: 2009-06-25
forum: General Help
---

### Post by chaopoch on 2009-06-25
I would like to unpack a .xpi file and to modify something in it, but how can I compress the .xpi_FILES back to a .xpi file?

Thanks for help.

---

### Post by VCoolio on 2009-06-25
Not sure if you can, but if you need to change the maximum firefox version in an add-on you can open the .xpi in file-roller (the archive-manager), then without extracting open the install.rdf in gedit, change anything, save and now file-roller will ask you what to do with detected changes, so save again. (there is also the Nightly Tester Tool add-on that will neglect incompatibility warnings while installing add-ons).
If this wasn't what you wanted I think the same goes for other files you want to change within a .xpi.

---

### Post by chaopoch on 2009-06-25
> **VCoolio said:**
> ...you can open the .xpi in file-roller (the archive-manager), then without extracting open the install.rdf in gedit, change anything, save and now file-roller will ask you what to do with detected changes, so save again...

Thanks, it works

---

