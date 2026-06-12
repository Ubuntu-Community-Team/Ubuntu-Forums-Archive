---
title: "Cinnamon System settings will not start"
date: 2019-04-19
forum: Desktop Environments
---

### Post by Redalien0304 on 2019-04-19
Have Ubuntu 18.04 With Cinnamon PPA Embryoson Added.
Everything was fine till Cinnamon 4 was updated, had earlier 3.8 cinnamon i believe.
tried cinnamon-settings & cinnamon-settings-info both giving me errors.


> cinnamon-settings


Traceback (most recent call last):
  File "/usr/share/cinnamon/cinnamon-settings/cinnamon-settings.py", line 619, in <module>
    window = MainWindow()
  File "/usr/share/cinnamon/cinnamon-settings/cinnamon-settings.py", line 247, in __init__
    for module in modules:
  File "/usr/share/cinnamon/cinnamon-settings/modules/cs_desktop.py", line 6, in <module>
    gi.require_version('Nemo', '3.0')
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 130, in require_version
    raise ValueError('Namespace %s not available' % namespace)
ValueError: Namespace Nemo not available 
Any is Help is Appreciated Thanks

---

### Post by Redalien0304 on 2019-04-19
BUMP Anyone??

---

### Post by Redalien0304 on 2019-04-21
Bump Anyone?? No one having Problems Cinnamon Settings??

---

### Post by Redalien0304 on 2019-04-22
[COLOR=#000000]So no one is having Problems Opening  Cinnamon Settings??[/COLOR]

---

### Post by #&amp;thj^% on 2019-04-22
Try commenting the part of the code that checks the Nemo version with "#" infront of line six of file "cs_desktop.py"
path found here: /usr/share/cinnamon/cinnamon-settings/modules/cs_desktop.py

To now look like:
```
#gi.require_version ( 'Nemo', '3.0')
```

---

### Post by #&amp;thj^% on 2019-04-24
I had wondered if you have tried this yet>>>Works here:
```
cinnamon-settings
libgoa-backend-1.0.so.1: cannot open shared object file: No such file or directory
Failed to load module: /usr/lib/cinnamon-control-center-1/panels/libonline-accounts.so
True
Using pam module (python3-pampy)
```
I used:
```
sudoedit /usr/share/cinnamon/cinnamon-settings/modules/cs_desktop.py

```
Commented the line as I suggested:
```
#!/usr/bin/python3

from gi.repository import Gio

import gi
**[COLOR="#FF0000"]#gi.require_version('Nemo', '3.0')[/COLOR]**

from GSettingsWidgets import *

DESKTOP_SCHEMA = "org.nemo.desktop"
LAYOUT_KEY = "desktop-layout"
ORPHANS_KEY = "show-orphaned-desktop-icons"

DESKTOPS_ON_PRIMARY = "true::false"
DESKTOPS_ON_ALL = "true::true"
DESKTOPS_ON_NON_PRIMARY = "false::true"
DESKTOPS_ON_NONE = "false::false"


class Module:

```
And my settings now show.

---

### Post by Redalien0304 on 2019-04-28
Ok Thanks 1fallen

"[COLOR=#000000][FONT=&quot]#gi.require_version ( 'Nemo', '3.0')"
 has solved my problem.[/FONT][/COLOR]

---

