---
title: "java logs"
date: 2009-01-23
forum: General Help
---

### Post by robofish on 2009-01-23
Hi,

I ran a java program by double clicking the jar icon and I need to check out the error messages.  Does anyone know where the log file would be?

Thanks.

---

### Post by squaregoldfish on 2009-01-23
Whether or not log files are created is up to the application, so check its documentation to see if it mentions anything on the subject.

Alternatively, you can run the jar from a terminal and see what's logged to the console:

```
java -jar <jarfile>
```

Steve.

---

### Post by robofish on 2009-01-29
Sorry, what I meant to ask was: If it writes to System.err and it's not run on the console, where does it write to?

---

### Post by squaregoldfish on 2009-01-30
That will be up to whatever window manager you're using, but in my experience, the output is ignored. Running from a console is the only way to see what console messages are being logged!

Steve.

---

