---
title: "Restricting Access to a folder and it's files"
date: 2009-03-18
forum: General Help
---

### Post by malfist on 2009-03-18
So I have this folder in /home/winLogger/Logs and I want to restrict it so only winLogger and members of the admin group can read/write to it. I don't want non-admins even able to read from it. How can I do this?

Thanks!

---

### Post by a fenderson on 2009-03-18
> chown winLogger:admin /home/winLogger/Logs

chmod 660 /home/winLogger/Logs

i think

---

### Post by malfist on 2009-03-18
Winlogger is not an admin, infact it isn't in any groups.

---

### Post by taurus on 2009-03-18
If you don't want anybody to look at your stuff in Logs, just change the permissions and only you can access that directory.

```
chmod 700 ~/Logs
ls -la
```

---

### Post by malfist on 2009-03-18
That worked, thanks!

---

