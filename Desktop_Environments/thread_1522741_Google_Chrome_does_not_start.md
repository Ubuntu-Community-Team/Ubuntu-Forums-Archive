---
title: "Google Chrome does not start"
date: 2010-07-02
forum: Desktop Environments
---

### Post by anieruddha on 2010-07-02
Hi

my google chrome browser does not start when I clicked on chrome icon. When I start to run using shell I got following error

[10390:10390:11208320785:FATAL:chrome/browser/zygote_host_linux.cc(127)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /opt/google/chrome/chrome-sandbox is mode 4755 and owned by root.
Aborted

I m using ubuntu 10.04 netbook.

---

### Post by anieruddha on 2010-07-02
sorry, I make hurry in posting thread, I found solution
here
[http://ubuntuforums.org/showthread.php?t=1346956&page=2](http://ubuntuforums.org/showthread.php?t=1346956&page=2)

just run 
sudo chmod 4755 /opt/google/chrome/chrome-sandbox
and now crome running fine. but can anybody please explain what that 4 means? and how
chmod 755 and chmod 4755 different

---

### Post by khelben1979 on 2010-07-02
```
man chmod
``` for manual page.

---

### Post by Geremia on 2013-03-17
I wasn't able to get it working by correcting the permissions; however, turning off sandboxing did enable Chrome to start:```
google-chrome --no-sandbox
```

---

### Post by varunendra on 2013-03-17
Old thread, closed!

---

