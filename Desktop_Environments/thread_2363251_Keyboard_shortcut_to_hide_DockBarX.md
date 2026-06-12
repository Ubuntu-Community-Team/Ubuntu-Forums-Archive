---
title: "Keyboard shortcut to hide DockBarX"
date: 2017-06-08
forum: Desktop Environments
---

### Post by nillmorais on 2017-06-08
Is there any way to hide the DockBarX using a keyboard shortcut?

---

### Post by again? on 2017-06-09
I don't know an easy way other than use a toggle script to kill and start.
Tested here in Ubuntu 17.04 this works.
Test this command both when dockx is running and not running to check it only shows PID when running.
```
ps aux | awk '/[d]ockx/{print $2; exit}'
```

If it works save this as **dockx-toggle.sh** and make executable.
```
#!/bin/bash

# click to start, click to stop

if ps aux | awk '/[d]ockx/{print $2; exit}' | grep [0-9] > /dev/null
	then
		killall dockx 
	else
		dockx
fi
exit 0
```
Bind the path to the script as a keyboard shortcut.

---

