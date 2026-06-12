---
title: "feed a fortune to kdialog as a welcome/login message"
date: 2005-07-10
forum: Desktop Environments
---

### Post by virgule on 2005-07-10
I want to use fortune and kdialog together. Fortune provides the kdialog content.. I want it to run upon login into KDE instead of the 'Did you know?' thing.
How does it work?

I imagine something simple along:
```

]$ fortune > kdialog --msgbox
or
kdialog --msgbox [&!'()fortune'"`!@&]

```

.:whistle:.

---

### Post by cwaldbieser on 2005-07-10
This simple script should do the trick:

```
#!/bin/bash

MSG=$(fortune)
kdialog --msgbox "$MSG"
```

Save this script in a file, give it executable permissions, and put it in your ~/.kde/Autostart folder.

---

