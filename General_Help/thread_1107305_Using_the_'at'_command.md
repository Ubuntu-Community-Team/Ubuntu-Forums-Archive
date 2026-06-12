---
title: "Using the 'at' command"
date: 2009-03-26
forum: General Help
---

### Post by 7raTEYdCql on 2009-03-26
Why doesnt the at command work with all applications.

```
at 6:30
evince filename.pdf
gedit abc.txt
...
```
It doesnt work.

But when i do ```
at 6:30
mplayer abc.wav
 
```

It works. Is there a difference in the application???

---

### Post by Wayne_V on 2009-03-26
evince and gedit require an X display -- per 'man at':

> The working directory, the environment (except for the variables
       TERM, DISPLAY and _) and the umask are retained from the time of invocation.

---

