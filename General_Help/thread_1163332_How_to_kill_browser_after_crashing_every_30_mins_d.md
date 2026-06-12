---
title: "How to kill browser after crashing every 30 mins due to flash"
date: 2009-05-18
forum: General Help
---

### Post by Toshikazu on 2009-05-18
Hi,Every 30mins to 1 hour of using flash my browser crashes. I can kill the process by window using xkill and clicking on it. But sometimes there is still an opera process running taking up 99% cpu usage. Killall opera never works, and kill [processid] only works 30% of the time now. And then I have to restart. Which is getting anoying. How would I kill such a process when those options fail? And also is there anyway to prevent flash from crashing and being unstable all the time.

Thank you

---

### Post by baseface on 2009-05-18
u want
```
kill -9
```

---

### Post by dfarrell07 on 2012-02-15
You'll need to find the Process ID (PID) of the browser before you can use kill. Run 

> ps -ef
or, if that is too much info this might work as well:
> top

Find the browser's process and look at the 2nd column. That is the PID of the process. Run

> kill -9 PID_HERE

---

### Post by cariboo on 2012-02-16
A 3 year old thread, is 3 years old. Even though the last post is valid, I think we should let this thread go back to sleep. Thread closed.

---

