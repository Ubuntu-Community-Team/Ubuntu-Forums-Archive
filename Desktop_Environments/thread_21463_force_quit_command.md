---
title: "force quit command"
date: 2005-03-22
forum: Desktop Environments
---

### Post by foobar on 2005-03-22
how do i 'force quit' an app' from the console?

---

### Post by lao_V on 2005-03-22
Ctrl-C
or 
Ctrl-Z!!!

---

### Post by Martin Witte on 2005-03-22
ctrl-z does not kill, it sends a program to the background. a better way imho is:
- find the process id with ps -fu <your yser id>| grep <the app you want to kill>, so if I want to kill  this firefox session I would give:
martin@ubuntu:~ $ ps -fu martin|grep firefox
martin    4278     1  4 19:05 ?        00:00:55 /usr/lib/mozilla-firefox/firefox-bin -a firefox -contentLocale US -UILocale en-US

then I would use kill to end it, kill needs the pid, here that is 4278, so we get:
martin@ubuntu:~ $ kill 4278

if this dows not work you try kill -9 4278.

hope this jhelps, Martin

---

### Post by az on 2005-03-22
you can also run top.

man top

It lists the running processes and alows you to kill them, among other things.

---

### Post by munki on 2005-03-22
Or if your in X, just enter 'xkill' in the prompt, and then click the application window to kill it :)

---

