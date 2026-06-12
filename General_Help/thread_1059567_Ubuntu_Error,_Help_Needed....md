---
title: "Ubuntu Error, Help Needed..."
date: 2009-02-03
forum: General Help
---

### Post by Pinejoker on 2009-02-03
Could anyone can help me to fix this error...


[IMG]http://img6.imageshack.us/img6/4361/screenshotim8.png

---

### Post by mb_webguy on 2009-02-03
What problem, exactly?  If it's just that AVG can't scan those few files and directories, make sure you're running AVG as root.

---

### Post by Pinejoker on 2009-02-03
how cam fix the errors.. i got avg. but its just scanning the error not fixing the errors..

---

### Post by jerome1232 on 2009-02-03
> **Pinejoker said:**
> how cam fix the errors.. i got avg. but its just scanning the error not fixing the errors..

Smaller pics my friend, all it's saying is it doesn't have permission to read those files. Probably because your running it as a regular user. Run it as root.

Hit alt+f2 then type:

```
gksu *command-that-would-normally-launch-avg*
```

---

### Post by Pinejoker on 2009-02-03
and then? what next ?? nothing happen.. still cannt open and i still have the errors..

---

### Post by jerome1232 on 2009-02-03
Scan it'll be able to read every file on your filesystem while running as root.

---

### Post by Pinejoker on 2009-02-03
is there a command to fix my errors...

---

### Post by mb_webguy on 2009-02-03
First, I don't see any errors.  AVG is not able to scan certain files, but it has not found any threats.

Second, even if it had found some threats, I believe AVG for Linux (unlike its Windows counterpart) is only a virus scanner, and has no ability to remove threats.  ClamTk (which is a GUI for the command-line scanner ClamAV) *does* have the ability to remove threats, so you may want to check it out.  You can find it in the repositories.

Third, why exactly are you using an anti-virus application, anyway?  You don't have to worry about getting viruses on Linux.  Unless you're dual-booting with Windows and don't want to risk infecting the Windows installation, you don't need a virus scanner.  Check out the link in my signature for more information about security on Ubuntu.

---

### Post by Pinejoker on 2009-02-03
its happen is i got so many errors some picture cant view.. and now i feel some slow.. and then i cant open some websie..

---

