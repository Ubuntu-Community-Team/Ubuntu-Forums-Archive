---
title: "Associate .doc files to MS Word"
date: 2011-03-10
forum: Desktop Environments
---

### Post by calande on 2011-03-10
Hi guys,

Here's what I use to launch Word when I open a .doc file. I ask Gnome to launch a file that is made executable and that contains:

```
#!/bin/bash
export WINEPREFIX="/home/charles/.wine-mso" && wine "/home/charles/.wine-mso/drive_c/Program Files/Microsoft Office/Office12/WINWORD.EXE" "`winepath -w "$@"`"
```

Edit according to your own environment. I hope this helps :)

---

