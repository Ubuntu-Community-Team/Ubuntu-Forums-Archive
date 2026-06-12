---
title: "Problem with libfreetype6-dev"
date: 2005-01-13
forum: General Help
---

### Post by kjkrum on 2005-01-13
The /usr/include/ft2build.h from libfreetype6-dev 1.2.7-2.1ubuntu1 tries to #include <freetype/config/ftheader.h>.  However, the file's actual location is /usr/include/**freetype2**/freetype/config/ftheader.h.  I worked around this by symlinking the freetype2/freetype directory.

---

