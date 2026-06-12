---
title: "X CPU usage out of control"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Swad on 2006-06-24
For reasons that I have no idea about, I have now had my laptop get taken over by X going crazy on me with CPU usage.  In both instances the laptop ran fantastic for a day or so and then it went nuts.  I've reinstalled from the ground up in both instances.  The laptop is an HP Compaq nc6230.  Here is the process as it appears in htop:

```
/usr/bin/x :0 -br -audit 0 -auth /var/lib/gdm:0.Xauth -nolisten tcp vt7
```

It almost seems some of my issues may coincide with my usage of VMware player (using the deb that one of the repos provides).  All day at work today my laptop was fine.  Then I get home tonight and it's chewing up 50% of the processor easily (the process listed above).  VMware player goes into a crawl and barely runs... most things taking many minutes to do.

I know this is all very vague but this has really set me off.  I'm about to write Ubuntu off for this laptop but I'd rather not if possible.  Can someone give me some clues as to what specifically about that X process I can look into to see what's chewing things up?

---

