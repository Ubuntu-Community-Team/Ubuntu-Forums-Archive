---
title: "Sound-Volume sre-setting."
date: 2005-06-28
forum: Desktop Environments
---

### Post by Ninnghizidha on 2005-06-28
Good morning!

Every time i enter my Ubuntu-Desktop i have to reset the PCM-Volume-Setting. It is at 99%, thus i changed it to 80% and saved the session. Is there a way around it?

Ninnghizidha.

---

### Post by Xian on 2005-06-28
There are some media applications that while running can change your sound levels and thus contribute to such issues, but if this is not the case then you should be able to save your setting with the following command in a terminal:
```
$ sudo alsactl store
```

---

