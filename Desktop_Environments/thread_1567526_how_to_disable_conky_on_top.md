---
title: "how to disable conky on top"
date: 2010-09-03
forum: Desktop Environments
---

### Post by xdeathcorex on 2010-09-03
how do i make this conky not to be on top of others on startup?
i have to killall conky then activate conky to use it normally.

[IMG]http://i.imgur.com/BpsSf.png[/IMG]

---

### Post by bra|10n on 2010-09-03
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes

---

### Post by nick_goodfate on 2010-09-04
You have to make it wait for a few seconds before it starts...

Create a file somewhere (for example /home/me/.conkyscript.sh) make it executable and paste in it these two lines ```
#!/bin/bash
sleep 60 && conky;
```

Then add it to your startup applications. (remove your current entry of conky from startup applications)

---

