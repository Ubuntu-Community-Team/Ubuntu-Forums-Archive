---
title: "emerald crash - is there a way to auto fix this?"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by vapore0n on 2007-11-01
So every no and then emerald crashes and the title bars disappear. To fix this I made an icon that runs "emerald --replace"

Is there a way to automate this? Like a script that detects that emerald died and runs emerald again?

---

### Post by Zorael on 2007-11-01
You could make a script that loops 'emerald --replace'.

```
#!/bin/bash

while true; do emerald --replace; sleep 1; done &
```

It should work. If you want to swap to another window decorator, you need to kill the process first. So name it 'emerald.start', or so, then either make a script with 'killall emerald.start' or type that in a terminal when you want to close it.

edit-- To clarify, it will not start emerald once a second, but rather if emerald closes it will wait one second and then restart it.

---

### Post by vapore0n on 2007-11-01
worked perfectly.
This should help for when I put ubuntu in my parent's computer.
Thanks

---

### Post by CareyB on 2007-11-23
Of course it restarts emerald once a second.  How do you think it doesn't?

---

### Post by kcyanks1 on 2007-11-26
Thanks for the tip.  Would it be OK to add this to System-Preferences-Sessions so that it is running at start up?  Thanks.

---

### Post by vapore0n on 2007-12-14
yes.
thats where I have it and it works wonderfully.

---

### Post by kcyanks1 on 2007-12-14
> **vapore0n said:**
> yes.
thats where I have it and it works wonderfully.


Great, thanks.  I actually already did it after posting, and it has worked well.  Glad you have had success also.

---

