---
title: "[SOLVED] Conky Uninterruptible"
date: 2008-01-14
forum: Desktop Effects &amp; Customization
---

### Post by firedrow on 2008-01-14
I'm having some issues with Conky on Gutsy.  I was having it disappear when I just placed conky in the startup (through Sessions).  So I did some reading and wrote a conkylaunch script.

```

#!/bin/sh

sleep 30 &&
conky
exit

```

This would launch it fine and it would quit disappearing after startup.  But now after a while it disappears and System Monitor shows it as Uninterruptible.  Not sure if it is after a length of time or after a certain program runs.  I have tried running just conky from terminal and the conkylaunch from terminal, I can't reproduce the error.  But if I let it run after poweron, no doubt it runs again.

I also just edited the script to change 
```

conky

```

to

```

conky -d -c /home/drowland/.conkyrc

```

Gonna hope this fixes it, but I will see if anyone else has had this problem.

---

### Post by firedrow on 2008-01-16
It was the ACPI section I was calling in Conky.  Something wasn't compatible.  I will see if I can figure something out.

---

