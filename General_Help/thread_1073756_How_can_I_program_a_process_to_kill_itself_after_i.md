---
title: "How can I program a process to kill itself after it is executed?"
date: 2009-02-18
forum: General Help
---

### Post by nbtrap on 2009-02-18
For instance, I've my computer programmed to run a script called, say, "starup.sh" which, in turn, executes the commands to run a program called, say, "startup."

However, if I view processes, I see that both starup.sh and startup are using up memory, but the only point of startup.sh is to call startup, so is there a command I can write in the startup.sh script that will kill itself when it is done executing all other commands? I've tried "killall startup.sh", but it apparently doesn't work from within its own script. If I write another script to kill startup.sh, then I won't be able to kill that script.

Obviously, I know how to kill a process, but I want my computer to do it for me when I boot up. Any ideas?

---

### Post by lha on 2009-02-19
Does
```

#!/bin/sh

startup &

```
in startup.sh do what you are looking for?

---

