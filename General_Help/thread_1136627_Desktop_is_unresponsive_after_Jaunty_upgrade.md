---
title: "Desktop is unresponsive after Jaunty upgrade"
date: 2009-04-25
forum: General Help
---

### Post by Quirion on 2009-04-25
I'm currently affected by [bug 366262]("https://bugs.launchpad.net/ubuntu/+bug/366262"). The described workaround works for me but I'd like to know how I can trigger it automatically instead of applying it at every boot.

Thanks in advance for your help.

---

### Post by ajgreeny on 2009-04-25
Write a simple shell script ```
#!/bin/bash
nautilus
```in a text editor, save it as *nautilus.sh* in your home, make it executable, and then set it to run at startup in Sessions.  That should do it.

---

### Post by Quirion on 2009-04-25
Thanks. It worked.

---

