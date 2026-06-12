---
title: "Lugaru hd no sound in maverick"
date: 2010-10-11
forum: Gaming &amp; Leisure
---

### Post by Rustybolts on 2010-10-11
When running Lugaru since Maverick upgrade i now get no sound, any one else had this problem or know of reason why? If i run from terminal i get the following error.
open /dev/[sound/]dsp: No such file or directory

---

### Post by Rustybolts on 2010-10-12
Solved this post solved it
[http://ubuntuforums.org/showthread.php?t=1592344](http://ubuntuforums.org/showthread.php?t=1592344)
By opening in terminal with following command
```
padsp "/home/[COLOR=Red]username[/COLOR]/lugaru/lugaru"
```

---

