---
title: "Time-killing scripts"
date: 2009-02-02
forum: General Help
---

### Post by LeboyX on 2009-02-02
I have several scripts I run which grade programs. However, in the case of an infinite loop, the script will be continue waiting for the program to finish (which it won't). Is there a command to give a script a limited amount of time to complete before being killed?

---

### Post by mgol on 2009-02-02
```

PROGRAM AND PARAMETERS &  # e.g. instead of "du -sm /" do "du -sm / &" - it'll run it in the background
sleep SECONDS             # if You want to wait SECONDS seconds before killing the script
kill $!                   # $! is the pid of the process run in the first line

```
If You want to brutally kill the script instead of terminating it, do:
```
kill -9 $!
``` or
```
kill -KILL $!
```
in the last line instead.

I'd rather advise first to try to terminate a process (maybe it'll cooperate) and only if it refuses (let's say, it will not terminate during one second), actually to kill it.

This would look like that:
```

PROGRAM AND PARAMETERS &
sleep SECONDS
kill $!
sleep 1
kill -9 $!

```

You can also make a script:
```

#!/bin/sh
SECONDS=10 # put here what You want
exec $1 &
sleep $SECONDS
kill $!
sleep 1
kill -9 $!

```
and invoke it each time by:
```
./script "PROGRAM AND PARAMETERS"
```

---

### Post by LeboyX on 2009-02-02
So, "sleep" won't pause the actual process, as the "&" moves it into the background, which is no longer affected by "sleep".

Am I following correctly?

---

### Post by mgol on 2009-02-02
> **LeboyX said:**
> So, "sleep" won't pause the actual process, as the "&" moves it into the background, which is no longer affected by "sleep".

Am I following correctly?

Yes. And the $! variable returns the PID of the last process run in the background in the current shell.

---

### Post by LeboyX on 2009-02-02
Hmmmm. O.k.

What if the process ended on its own (no infinite loop). It looks like this implementation would still kill the process. Or, if the process is already completed, will the kill simply fail (as its target is no longer running) and the script just continue like everything's alright?

---

### Post by mgol on 2009-02-03
Kill will just exit immediately with the error code different than 0. Actually, it will be quite often as if the process terminates properly then the "kill -9" won't find it. The exit code of the last command is also the exit code of the whole script. You may not want the whole script to return error codes. If that's true, just add 'exit 0' as the last line of the script

---

