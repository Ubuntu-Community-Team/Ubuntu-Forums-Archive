---
title: "gamin 0.1.2"
date: 2005-07-23
forum: Deferred/Invalid Requests
---

### Post by nicokaiser on 2005-07-23
gamin in a File and directory monitoring system.

The current version in Hoary (0.0.26) has major problems with files > 2gb and it sometimes breaks horribly (consumes all CPU, etc.). Version 0.1.2 (from Breezy) can be compiled without any problems and without any dependency problems, and it seems to work better...

---

### Post by jdong on 2005-07-24
[http://packages.ubuntu.com/breezy/source/gamin](http://packages.ubuntu.com/breezy/source/gamin)

Gamin exports a library (libgamin). The new one is not binary compatible with Hoary's, so any programs compiled against the new libgamin will likely need recompiling. This is not qualified for backporting, as a result.

---

