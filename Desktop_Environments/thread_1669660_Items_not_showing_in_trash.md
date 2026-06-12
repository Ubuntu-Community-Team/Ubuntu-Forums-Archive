---
title: "Items not showing in trash"
date: 2011-01-18
forum: Desktop Environments
---

### Post by julius.tupino on 2011-01-18
Hi everyone;

I am a newbie here. I have a problem with my Ubuntu 10.4. When I move my mouse over the trash folder it says some items are in there but when you look in the trash folder it's completely blank. Without any items. 

I've tried searching for some solutions but couldn't find any. I hope someone from here may be able to help me or assist me in trouble-shooting this problem.

Thank you all in advance.

---

### Post by Elfy on 2011-01-18
Hi - lets see if there is anything in there, open a terminal from the appc accessories menu and run this command

```
ls -al ~/.local/share/Trash/files/*
```

Does that show anything?

---

### Post by Hat-trick on 2011-08-10
Sorry to bump an old thread.  I went into the terminal and it states

ls: cannot access /home/hat-trick/.local/share/Trash/files/*: No such file or directory

---

### Post by mister_p_1998 on 2011-08-11
I get this now and again in 8.04, it goes away after a reboot.

---

