---
title: "firefox under ssh X11 forwarding kills local firefox"
date: 2007-10-09
forum: Desktop Environments
---

### Post by blurp on 2007-10-09
Now, I already have firefox running on the local machine. For some reason, I needed to run another instance of firefox over ssh X11 forwarding from another machine. 

If I do this
```
user@remote:~$ firefox
```
a new local firefox browser window will appear.

But if I do this
```
user@remote:/usr/lib/firefox$ LD_LIBRARY_PATH=. ./firefox-bin
```
the remote machine's firefox will run, but the local firefox crashes.

Why?

---

