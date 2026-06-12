---
title: "KDevelop Error"
date: 2006-08-01
forum: Desktop Environments
---

### Post by mikesena on 2006-08-01
Hi,

I am trying to make a kde application in kdevelop.  However, it outputs this error:
```

checking for Qt... 
configure: error: Qt (>= Qt 3.2) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!
*** Exited with status: 1 ***

```
I have checked, qt-mm is installed but not qt-mm-dev.  ubuntu won't let me install dev, because the qt-mm is a newer version (apparantly).


What should I do and how can I fix it?

---

### Post by umuro on 2006-08-17
Yes. Help. The same problem for me. It's the first time I will try KDevelop and I cannot do anything.

---

### Post by philippe_carlo on 2006-08-17
Download and build Qt from the sources at [http://www.trolltech.com/developer/downloads/qtopia/coregpl]("http://www.trolltech.com/developer/downloads/qtopia/coregpl")
and make sure to compile it with multi-threading support. Use environment variables (as documented) to override your already installed version of QT. I strongly advise to keep the new version completely separate from the system by intsalling in /usr/local.

---

