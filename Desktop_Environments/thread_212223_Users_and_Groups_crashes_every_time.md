---
title: "Users and Groups crashes every time"
date: 2006-07-09
forum: Desktop Environments
---

### Post by nosam on 2006-07-09
Every time I have tried to open System>Administration>Users and Groups the box pops up but sits there empty and inaccesible with the mouse icon "working" until I get the "not responding" dialog and have to force close the window.  This happens every single time.  I also am having the exact same problem when I try to open "Adjust Date & Time", whether from the panel option or from System>Administration>Time and Date.  Those are the only two that I've had trouble with so far... but I haven't played with everything as I'm new to ubuntu and just recently installed it.  Any ideas as to what the problem is?  Thanks.

---

### Post by nosam on 2006-07-10
Bump.  Anybody have any suggestions?

---

### Post by aysiu on 2006-07-10
Can you post the terminal output of this command? ```
gksudo users-admin
```

---

### Post by nosam on 2006-07-10
> **aysiu said:**
> Can you post the terminal output of this command? ```
gksudo users-admin
```

```
matt@matt-desktop:~$ gksudo users-admin
(users-admin:5479): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

---

### Post by aysiu on 2006-07-10
Does a window launch? Does anything happen?

---

### Post by nosam on 2006-07-10
> **aysiu said:**
> Does a window launch?

Yes.  But it does the exact same thing.

---

### Post by aysiu on 2006-07-10
I have no idea. I did some searching around for your error, but nothing was similar to your situation.

---

### Post by nosam on 2006-07-10
> **aysiu said:**
> I have no idea. I did some searching around for your error, but nothing was similar to your situation.

Oh well.  Thanks for your help though.

---

### Post by aysiu on 2006-07-10
> **nosam said:**
> Oh well.  Thanks for your help though.
I wish I had some clever fix.

---

