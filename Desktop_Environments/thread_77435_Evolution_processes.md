---
title: "Evolution processes"
date: 2005-10-16
forum: Desktop Environments
---

### Post by ow50 on 2005-10-16
I noticed that I have two Evolution processes continuously running in the background: "evolution-data-server-1.4" and "evolution-alarm-notify", both of which take around 57 MB memory.

I use Evolution only for reading mail and newsgroups. I'm not fully sure what those two processes do, but I can't see myself needing them. I can kill them, but they restart every time I start Evolution.

Is there a clean way to disable them or should I just write a shell script for starting Evolution that would kill those processes after a short period of time has passed since Evolution has been closed?

---

### Post by ow50 on 2005-10-17
Going with the shell script
```
#!/bin/bash

# Start Evolution and close by-product processes upon quit.

evolution --component=mail
killall evolution-data-server-1.4
killall evolution-alarm-notify
```

Edit:
It doesn't work, the processes reappear. Secondly, the actual memory usage is less than 5 MB for both processes. I was looking at the wrong memory column in the system monitor.

---

