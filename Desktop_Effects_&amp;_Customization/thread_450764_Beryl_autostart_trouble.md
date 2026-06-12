---
title: "Beryl autostart trouble"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by Jango on 2007-05-21
Hey,

I use Feisty Fawn and Beryl seems to work just fine until I try to add it to autostart in sessions. If I do so and reboot, after logging it it would say that the "last session lasted less than 10 seconds and blah-blah" and get me to the logging screen again.

Is there a way to fix it?
Thanks!

---

### Post by Jango on 2007-05-21
Solved!
In case u have the same problem:
Make a script, that looks like that:

```

#!/bin/bash
sleep 2
beryl-manager

```

Don't forget to make it executable. Add it to GNOME sessions. Worked fine for me.

---

