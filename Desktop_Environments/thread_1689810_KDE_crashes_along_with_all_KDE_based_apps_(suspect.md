---
title: "KDE crashes along with all KDE based apps (suspected d-bus error)"
date: 2011-02-17
forum: Desktop Environments
---

### Post by Durduran on 2011-02-17
Hi, my desktop decided one day to simply die and not start, whenever I log-in, KDE starts loading then promptly crashes and falls back to login screen.

I was unable to find anything useful in logs, but I installed Xfce which runs ok ... however when I start any KDE app under it, it crashes with a message:

```
<unknown program name>(23097)/: Communication problem with  "dolphin" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.dolphin was not provided by any .service files" "
```

This seems to be a D-BUS issue, can anyone help in resolving it? ;)

Thanks

---

### Post by Durduran on 2011-02-17
Oh, so I've found the solution ... it's a weird one. All that's needed is to delete some temporary KDE cache files:

sudo rm -rf /var/tmp/kdecache-*

I've found the solution here: [http://ubuntucomputing.posterous.com/fixing-orgfreedesktopdbuserrorserviceunknown](http://ubuntucomputing.posterous.com/fixing-orgfreedesktopdbuserrorserviceunknown)

---

