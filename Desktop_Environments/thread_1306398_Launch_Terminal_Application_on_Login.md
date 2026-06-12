---
title: "Launch Terminal Application on Login"
date: 2009-10-30
forum: Desktop Environments
---

### Post by deejross on 2009-10-30
I have a Mono terminal application that needs to run on login, but adding it using System -> Preferences -> Startup Applications doesn't start it. If it does, I can't see, but I NEED to be able to see the application. It does me no good if I can't see it.

I tried writing a bash script that runs it like this:
```
gnome-terminal --command="mono application.exe"
```
But I get an message box saying that gnome-terminal is having an error launching a child process or something like that.

Right now, I have the following bash script that works if I double-click on it from the Desktop and choose Display in Terminal, but fails to launch when added to Startup Application:
```

#!/bin/bash
cd ~/appDirectory
mono application.exe

```

Can someone help me with this? Oh, and I'm running Ubuntu 9.04.

---

