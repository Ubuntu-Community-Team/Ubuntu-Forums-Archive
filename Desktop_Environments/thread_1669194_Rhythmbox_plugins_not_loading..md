---
title: "Rhythmbox plugins not loading."
date: 2011-01-17
forum: Desktop Environments
---

### Post by MarkVS on 2011-01-17
While using Rhythmbox this morning, I was greeted by a blunt and undiscriptive error message:

```
Plugin Error:
Unable to activate plugin Cover Art.
```

Going to the plugin page, I was supprised to find that most of the installed plugins would not load. Without any info being offered in the player, I looked on line. Many people had problems with other plugins, and most of the time it was a problem with an uninstalled python package. But I checked on this site and I found that I had all of these packages installed. (Well, the python ones at least, to check all of them would take forever.)
```
http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=472849
```

After finding no help there, I ran rhythmbox -d to debug:

```
(12:04:33) [0x934fe68] [rb_python_module_init] rb-python-module.c:406: Init of python module

(rhythmbox:4971): Rhythmbox-WARNING **: unable to load module as python runtime could not be initialized

(rhythmbox:4971): Rhythmbox-WARNING **: Could not load plugin artflow

(12:04:33) [0x934fe68] [rb_python_module_finalize] rb-python-module.c:413: Finalizing python module (null)

(rhythmbox:4971): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Art flow'
(12:04:33) [0x934fe68] [plugin_manager_set_active] rb-plugin-manager.c:306: Could not activate Art flow.
```

Ok, so python isn't loading. But I have all of the right python packages. So WHY aren't they loading? I am lost now.

---

### Post by MarkVS on 2011-03-01
After a long, time I found the solution. Whatever was causing my plugins to fail was also causing my Update Manager and Software Center to fail as well. So I searched under those. The problem? Python was corrupted. Easy fix; just open synaptic, search under "python", and reinstall everything that comes up already installed. It works!

---

