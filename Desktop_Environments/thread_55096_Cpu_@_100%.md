---
title: "Cpu @ 100%"
date: 2005-08-07
forum: Desktop Environments
---

### Post by wadesmart on 2005-08-07
08072005 1241 GMT-5

This morning I woke to find that the cpu was 100% but nothing was running. I opened System Monitor and Nautilus was at 99% constant. After two hours of this I finally rebooted the system. Things were ok for a while. I checked my email and browsed a few sites but then all of the sudden it did it again. 

First, has anyone else had this problem?

Second, what can one do when this happens? Rebooting surely isnt the answer. 

Wade

---

### Post by cwaldbieser on 2005-08-07
Don't know why it is happening, but you shouldn't have to reboot.  You should be able to just kill nautilus, I think.  From the terminal try:

```
$ skill -KILL -i nautilus
```

It will show you each nautilus process running and prompt you ("y" or "n") to kill each one.

Alternatively, from the GUI, Applications -> System Tools -> System Monitor -> Processes Tab.  Select nautilus and choose the "End Process" button.

When you kill nautilus, a new one is respawned, which hopefully won't be gobbling up your CPU.

---

### Post by minio on 2005-08-07
This how I usually kill nautilus: 
```
killall -9 nautilus
``` 
from console

---

