---
title: "[SOLVED] Different Startup Programs Based on Session Type?"
date: 2008-06-04
forum: Desktop Environments
---

### Post by pmaconi on 2008-06-04
Is it possible to have different startup programs based on the GDM Session type?

For example, right now I'm playing with Gnome/Openbox, but don't want my Openbox configuration to screw up my standard Gnome configuration. I'm looking for a way to have Gnome/Openbox run a conky script made to use Openbox whenever I start that type of session. But I also want a normal Gnome session to start a different conky (that works with compiz). Is this possible?

---

### Post by sdennie on 2008-06-05
I've not used OpenBox but, if they are sharing the same startup scripts, one thing you could do would be to write a script that detects the window manager and decides what program to run.  You'll probably have to delay the script so as to make sure the WM is running.  Something like this perhaps:

```

#!/bin/bash

sleep 10

if pgrep openbox ; then
    # Start a program for openbox
else
    # Start a program for gnome
fi

```

---

### Post by pmaconi on 2008-06-05
Thanks! I'll give it a try this weekend.

---

