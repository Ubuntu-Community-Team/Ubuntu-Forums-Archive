---
title: "Gnome login problem"
date: 2005-09-15
forum: Desktop Environments
---

### Post by dphipps on 2005-09-15
When I try to log it the session terminates and I get an errer messege that it was unable to read ICE authority file : /home/phipps/.ICEauthority.  Does anybody know what could cause this to happen and how I could fix it?

---

### Post by FLeiXiuS on 2005-09-15
```
$ sudo chmod 644 /home/phipps/.ICEauthority
```

That should solve your problems.  If not please paste the output of 

```
$ ls -al ~/.ICEauthority
```

---

### Post by dphipps on 2005-09-15
I fixed my problem.  The file was owned by and readable only by root.  I changed the ownership on the file and was than able to log on as normal.

---

