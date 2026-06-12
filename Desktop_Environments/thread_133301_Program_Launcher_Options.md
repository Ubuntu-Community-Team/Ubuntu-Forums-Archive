---
title: "Program Launcher Options"
date: 2006-02-19
forum: Desktop Environments
---

### Post by RedTDI on 2006-02-19
How can I duplicate the Windows "Start In directory" option in a Gnome Launcher that starts a Windows Program running under Wine.

In trying out the KDE Desktop and Launcher, their options allow a Working Directory option which effectively is the same as the Windows Start In Directory.

I have tried numerous ways to add the information but nothing seems to work in the Gnome Launcher.

Or can this feature not be duplicated in the Gnome Launcher?

Dennis

---

### Post by Ptero-4 on 2006-02-19
AFAIK it can't. The gnome dev team cut off way too much of gnome and left it less than ideal, plus they're feature-nazis.

---

### Post by RAOF on 2006-02-19
I'm not quite sure why you'd want to, but I think you should be able to do it with a bash script.  Something like
```

#!/bin/sh
cd path_to_working_directory
program_to_run

```
and then making a menu entry for the shell script.

---

