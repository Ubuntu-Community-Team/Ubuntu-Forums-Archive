---
title: "11xvnc"
date: 2008-12-24
forum: Desktop Environments
---

### Post by num on 2008-12-24
hello,

i installed x11vnc but i am having issues running it. is there a good tutorial anywhere on how to use it?

---

### Post by s3gfault on 2008-12-24
i haven't seen one.  are you getting error messages?  check the manpage that came in the package
```
man x11vnc
```
some things to keep in mind
1) make sure you firewall allows connections on whatever port your hosting the service on, i think 5900 or 5901 is default.
2) you vnc client may also have interesting error messages to help diagnose the problem

---

