---
title: "CALMTK antivirus intallation and update"
date: 2009-04-27
forum: General Help
---

### Post by deerhunter on 2009-04-27
I have been trying to install the antivirus CLAMTK but I cannot get it to update the fvirus definition. It days that I need to be the root to do it. Can anyone help me with this?

---

### Post by bacardiandwatermelon on 2009-04-27
Same issue as this thread?

[http://ubuntuforums.org/showthread.php?t=445343]("http://ubuntuforums.org/showthread.php?t=445343")

---

### Post by cariboo on 2009-04-27
Open an Applications-->Accessories-->Termianl and type:

```
sudo freshclam
```

this will create a cron job that checks for updates daily.

---

### Post by deerhunter on 2009-04-27
Thanks that worked

---

