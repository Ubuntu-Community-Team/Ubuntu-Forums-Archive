---
title: "find --invert-match option?"
date: 2009-05-20
forum: General Help
---

### Post by milasch on 2009-05-20
Is there a way of finding files with a name pattern not including a second name pattern and executing a command for that?

example:

```

find . -name "pattern1" **-invert-option "pattern2"** -exec cp {} /tmp \;

```

In the example above I would copy all files **RECURSIVELY** with name pattern1 and excluding all name pattern2 to tmp folder.

No scripts allowed.

Thanks

---

