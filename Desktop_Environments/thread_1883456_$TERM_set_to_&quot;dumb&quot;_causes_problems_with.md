---
title: "$TERM set to &quot;dumb&quot; causes problems with suspend"
date: 2011-11-19
forum: Desktop Environments
---

### Post by julkopki on 2011-11-19
Hello everyone.

I've just upgraded from 11.04 to 11.10. So far I love it, everything seems just so much snappier.

Now I just have one minor issue. When I try to "suspend" my laptop, it doesn't work - instead it fades out the screen, blocks it and then instantly wakes back.

I've checked the logs in /var/log/pm-suspend.log and this fragment seems relevant:

```

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00clear suspend suspend:
TERM environment variable not set.

/usr/lib/pm-utils/sleep.d/00clear suspend suspend: Returned exit code 1.
Sat Nov 19 12:23:20 CET 2011: Inhibit found, will not perform suspend
Sat Nov 19 12:23:20 CET 2011: Running hooks for resume

```

The mentioned script at /usr/lib/pm-utils/sleep.d/00clear reads:

```

#!/bin/bash
clear

```

When I open a terminal anywhere by hand, $TERM is set to either "linux" or "xterm". However somehow when the 00clear command is executed $TERM is set to "dumb".

Two questions:
- What is the correct value for $TERM when running 00clear script?
- Where can I set it up?

PS: I've looked for solutions on the web, however no success so far.

---

