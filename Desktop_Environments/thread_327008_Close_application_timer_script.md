---
title: "Close application timer script"
date: 2006-12-28
forum: Desktop Environments
---

### Post by marianlibrarian on 2006-12-28
I will be installing new computers in our library with Ubuntu or Edbuntu. I currently run our computers on windows 98. I have a script that closes the browser after 1 hour. Each patron is allowed 1 hour at a time. Since I will have 6 machines for public access and 1 librarian, it really helps to have a script controlling the time an application stays open. I am open to a timer script that maybe has a sound that occurs when the time is up too. That way it gets my attention just in case they just let the browser close and simply open a new session. 

Thanks!

---

### Post by kidders on 2006-12-28
Hi there,

You could base a script around something like this, if you liked...

```
ssh user@host.name killall opera
```

You would set up key-based authentication, so the command could be issued non-interactively, to terminate applications remotely.

Alternatively, you could operate the script locally, perhaps by starting browsers this way...

```

#!/bin/bash
/usr/bin/opera&
PID=$!
sleep 3600
kill $PID

```

Of course, either approach would be dressed up with friendly-looking notification messages and maybe some pretty sound effects.

Does either of these take your fancy? Would you prefer a locally or remotely controlled approach?

---

### Post by marianlibrarian on 2006-12-28
I think the second example is closer to what I want. It looks like it will behave similar to what I already have. To have the timer start when the browser window is opened. It stays active for one hour and then closes. I also have a warning at the 5 minute mark to let patrons know that the browser window will close in 5 minutes. 

Thanks!

---

### Post by kidders on 2006-12-29
No problem :-)

May I suggest that, once you've made your timer script, you share it with the library's machines over NFS, so you don't have to worry about updating multiple computers every time you tweak it. You could also maybe share browser plugins, so you won't have to install the same things over and over.

Depending on your graphical environment, apps like kdialog would be handy for displaying warning messages, or perhaps you could record yourself saying "5 minutes to go!", and do something like "echo warning.wav > /dev/dsp" (depending on your sound system).

---

