---
title: "Change display of already runnig process"
date: 2012-05-20
forum: Desktop Environments
---

### Post by rblsfx on 2012-05-20
Hello folks,

Is there a way to change display of already runnig process? What I mean is that you can run program on different displays (not necessarily the one you are currently on) like:
```
$ DISPLAY=:0 gedit &
```

That way you can launch application in display associated with different gnome session. But is there a way to change display for already running process without having to kill it and re-run it?

Also additional question about nohup. If I do the same with nohup:
```
$ nohup DISPLAY=:0 gedit &
```

I get error:
```
$ nohup: ignoring input and appending output to `nohup.out'
nohup: failed to run command `DISPLAY=:0': No such file or directory
```

Is there a way to pass display parameter using nohup?

---

