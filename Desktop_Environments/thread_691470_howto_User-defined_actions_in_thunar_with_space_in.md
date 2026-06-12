---
title: "howto User-defined actions in thunar with space in parameter?"
date: 2008-02-08
forum: Desktop Environments
---

### Post by Doc_symbiosis on 2008-02-08
Hi there,

I want to write ( already have ) written a script for user-defined actions in thunar. Anyway, I want to be able, to pass filenames with spaces in the name to this script.

to keep it simple, here an example script
```

#!/bin/bash
for file in $* ; do
        echo $file 
done
read

```
In the user-defined actions, I made the following entry as command
```

xfce4-terminal -x  ~/test.sh %f

```
it works so far, but only, if there are no spaces in the filename.
How do I get thunar, to pass the filename with doublequotes enclosed?
 I already tried "%f"    '%f'     \"%f\"

---

### Post by tcommbee on 2008-02-08
i don't think passing the arguments is wrong, but already the auto-insertion, which replaces %f with the filename (or only the first part of it as i think). this would also be consistent with your attempts of escaping the path yourself.

---

