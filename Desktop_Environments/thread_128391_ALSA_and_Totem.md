---
title: "ALSA and Totem??"
date: 2006-02-11
forum: Desktop Environments
---

### Post by dalani on 2006-02-11
Whenever I try using Totem to play MP3, I keep getting the following message:
Code:

ALSA device "default" is already in use by another program.


CAn anyone elucidate this??
__________________

---

### Post by TitusDalwards on 2006-03-11
any program is using the alsa default inte terminal you can type ```
 ps x
```
and then you will see PID numbers find the alsa using program and type
```
kill PID_num
```

---

