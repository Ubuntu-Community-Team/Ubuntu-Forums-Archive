---
title: "Matlab cannot interrupt execution of loop"
date: 2005-11-03
forum: Desktop Environments
---

### Post by makhand on 2005-11-03
I have a very weird matlab problem. I have Matlab R14 SP3 on breezy. For some reason, I cannot interrupt a routine/mfile/loop/etc while it is executing using the usual 'Ctrl-C'. Actually, i just tried to do this same thing using the '-nodesktop' option (terminal mode) and the problem doesnt exist. Has anyone encountered this problem? You can check by doing something like: 
```

for i = 1:300000
i
end
```
While it is outputting these, try to halt matlab by pressing Ctrl-C.
This problem makes it a bit difficult to debug. If you made a mistake, you're going to have to wait till the program finishes, no matter how long. The only thing I've been able to do to make it stop is to kill matlab, then start all over again. kind of annoying. help

---

### Post by Spie on 2005-11-03
When the "command window" is focused I can stop the loop by pressing ctrl+C. No problem.

---

### Post by makhand on 2005-11-03
Spie, what version of matlab? 
No such luck for me. I can press Ctrl-C 'till i'm blue in the face (:confused:) with no response.

---

### Post by makhand on 2005-11-03
Wow, now this is weird. I've discovered that this problem only exists when Matlab is running in secondary monitor. If i run it on the first screen (main monitor), it responds just fine. So it must be a bug that is not giving the matlab command window propper focus? Where do i go from here?

---

