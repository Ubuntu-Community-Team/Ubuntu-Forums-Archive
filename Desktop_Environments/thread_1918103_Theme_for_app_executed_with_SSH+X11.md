---
title: "Theme for app executed with SSH+X11"
date: 2012-01-31
forum: Desktop Environments
---

### Post by DarkLordSauron on 2012-01-31
Hi everyone,

I've developed an app with QT. When I execute this app in local, I get  something like the "local.jpg" image attached. But when I execute it  using SSH+X11 I get something like the "remote.jpg" image. I think SSH  changes the theme.
Do you know how can I avoid this behavior. I prefer the remote  look&feel, but I don't mind if I only get the local one. I just want  to avoid it changes.

Both remote and local systems are Ubuntu.

Thanks in advance!

---

### Post by DarkLordSauron on 2012-02-02
I've found the problem.
 It's related with QT style. A bug in QT or something like that.

 I've installed qtconfig. If GUI Style is set to "Desktop Settings  (Default)" and I run my app with my user, it results as expected. But if  I run my app with "sudo" it uses such a "default" style of QT. This  default style is the same when I run my app with "gksu".
 
 If I change the GUI Style in qtconfig to any other, then "sudo" and  "no-sudo" executions yield the same result, same style. "gksu" has its own style. I  can force gksu to use the same style linking the  ~/.config/Trolltech.conf file to /root.config/Trolltech.conf
 ```
sudo ln ~/.config/Trolltech.conf /root.config/
```The matter is that running something from ssh with X11 the behavior is the same as with "sudo".

Regards

P.S.: I've reported [the bug]("https://bugreports.qt-project.org/browse/QTBUG-24045").

---

