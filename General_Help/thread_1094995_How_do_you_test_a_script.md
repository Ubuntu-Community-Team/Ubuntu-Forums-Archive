---
title: "How do you test a script?"
date: 2009-03-13
forum: General Help
---

### Post by nothingspecial on 2009-03-13
without out it doing what it`s supposed to do?

thanks

---

### Post by lloyd_b on 2009-03-13
If the script modifies files, copy the "live" files to a test directory, and run the script there (so you don't risk damaging the "live" files).

You can replace potentially "harmful" commands (such as "rm") with an "echo Not removing file" so that you can see what the script would be deleting.

Other than that, it depends a lot on exactly what the script is doing...

Lloyd B.

---

### Post by roccivic on 2009-03-13
Use a liveCD (and, if mounted, unmount all drives/partitions).

Peace.

---

### Post by nothingspecial on 2009-03-13
Cheers guys:D

---

