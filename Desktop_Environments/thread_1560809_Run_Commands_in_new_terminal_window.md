---
title: "Run Commands in new terminal window"
date: 2010-08-25
forum: Desktop Environments
---

### Post by uchacker11 on 2010-08-25
Is there a way that I can have a bash script run a set of commands in a new terminal window and continue the script in the current terminal window?  I know in windows I can run Start Cmd /C "commands" but I haven't been able to find a way to do this from a terminal in linux?

It would be really helpful to get this working.  I am trying to write a script that will allow me to SSH into my servers and its a pain opening a new terminal and typing out all the commands every time.

---

### Post by dv3500ea on 2010-08-25
Split those commands into a separate script (I'll use ~/script.sh for this example).

use:
```

gnome-terminal -e '~/script.sh' &

```

---

