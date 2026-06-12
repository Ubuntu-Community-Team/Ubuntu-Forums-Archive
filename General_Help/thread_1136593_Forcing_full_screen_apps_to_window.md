---
title: "Forcing full screen apps to window"
date: 2009-04-25
forum: General Help
---

### Post by tunads on 2009-04-25
In Windows there is a command line flag that forces an application to window. /windowed is the flag, and you can optionally force the size using /res (i.e. appName /windowed /res800x600x32). Is there an equivalent way of doing this in Linux?

---

### Post by fahadsadah on 2009-04-25
-windowed works with some apps.

---

### Post by tunads on 2009-04-25
> **fahadsadah said:**
> -windowed works with some apps.
That didn't work.

The program I am trying to start is a java app. They recommend you start it via the script they provide. Here is the code for the script:
```
#!/bin/sh
export LD_LIBRARY_PATH=./
java -cp ./cultris.jar -Djava.library.path=./ -Djexepack.resdir=./ Cultris $*
exit 0
```
Is there a way to modify the script to force the app to window?

---

