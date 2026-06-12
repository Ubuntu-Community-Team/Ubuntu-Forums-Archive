---
title: "Desktop display messed up"
date: 2012-01-12
forum: Desktop Environments
---

### Post by Hekabe on 2012-01-12
Hello,
after i ran [this script]("http://ubuntuforums.org/showthread.php?t=1726735"), I can no longer get to my desktop on Xfce or Xubuntu sessions. It just displays a gray screen with none of my icons. I can still use the bottom hoverdock normally, but if i click anywhere on the top bar, it just disappears and comes back after a second, without doing anything. I can still run things from the terminal, so I'm getting along ok, but it's a little frustrating.

I'm running 11.10 on a very old Dell tower (512 MB RAM), could this be the problem?

---

### Post by Toz on 2012-01-12
Is xfdesktop running?
```
ps -ef | grep xfdesktop | grep -v grep
```

If not, try starting it up:
```
xfdesktop --display :0.0
```

---

