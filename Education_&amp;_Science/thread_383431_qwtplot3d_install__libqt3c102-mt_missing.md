---
title: "qwtplot3d install:  libqt3c102-mt missing"
date: 2007-03-13
forum: Education &amp; Science
---

### Post by der_vegi on 2007-03-13
hi, out there!

i want to install qtiplot-0.8.9 - which is a great program for physics - from a debian sarge addon repository. qtiplot depends on qwtplot3d, but i cant install the debian package because it depends on  libqt3c102-mt, which isn't contained in ubuntu edgy.

does anyone know where i can get  libqt3c102-mt?

thanks for the help!

---

### Post by DrOlaf on 2007-03-13
libqt3c102-mt has been superseded by libqt3-mt. You could try installing that, and see if it works. That is in the edgy repos.

---

### Post by der_vegi on 2007-03-13
ah, thanks. i've done a kind of dirty hack:
installed qwtplot3d and qtiplot via dpkg --force and then changed the dependencies of the broken packages qwtplot3d and qtiplot in ```
/var/lib/dkpg/status
``` from libqt3c102-mt to libqt3-mt and the qtiplot dependency from liborigin to labplot, as labplot also provides liborigin.

---

