---
title: "Run program at startup, in terminal"
date: 2012-04-21
forum: Desktop Environments
---

### Post by tb189 on 2012-04-21
Hi,

I find many posts and how tos on how to add a program to sessions so it starts when you start ubuntu. However, I would like to run a program in the terminal window, so I can see any error messages afterwards. Do you know if theres a command to enter in startup applications, or is there some other way?

Thanks!

---

### Post by tb189 on 2012-04-21
Also, is it possible to time this, so one program starts a few seconds before the other?

---

### Post by hakermania on 2012-04-21
That's what you need to add to the startup applications:
```

gnome-terminal -e "./start.sh" --working-directory "/home/alex/Documents"

```This will open a terminal window running /home/alex/Documents/start.sh

Now, for your other problem, start.sh could be a script that would open the one process, wait a timeout using 'sleep' command and then launch the other application.

---

