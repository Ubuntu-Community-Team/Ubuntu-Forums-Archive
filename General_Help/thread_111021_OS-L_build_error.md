---
title: "OS-L build error"
date: 2006-01-01
forum: General Help
---

### Post by Basu on 2006-01-01
i tried to build the OS-L icon set but I get this error:

This script builds an installable KDE iconset using bash and convert.
Change what you want, add additional sizes, whatever... :)

Checking for bzip2... found /usr/bin/bzip2
Checking for tar...  found /bin/tar
Checking for convert...  no.

No convert found in path.

Please help
Thanks

---

### Post by cylon359 on 2006-01-01
convert is from ImageMagick

Try this first:  sudo apt-get install imagemagick

---

### Post by Basu on 2006-01-02
That did it. Thanks

---

