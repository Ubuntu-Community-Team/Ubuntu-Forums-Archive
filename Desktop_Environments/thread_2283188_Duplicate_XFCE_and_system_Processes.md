---
title: "Duplicate XFCE and system Processes"
date: 2015-06-19
forum: Desktop Environments
---

### Post by nonkreon on 2015-06-19
Hi everyone!
When I open XFCE task manager, I see the anomaly in the picture attached, where all tasks related to xfce and most system components are running with duplicates :( Note that "Show all processes" is not selected. Is this perfectly normal or am I running something like double sessions?
Thank you very much!

---

### Post by Toz on 2015-06-19
You should only have one of each of those processes running unless you have 2 user sessions currently connected/running. If you select the "UID" option from the settings menu it will show you which user id belongs to each process.

Also running the command "w" in a terminal window will show you who is logged in and where.

---

### Post by nonkreon on 2015-06-20
> **Toz said:**
> You should only have one of each of those processes running unless you have 2 user sessions currently connected/running. If you select the "UID" option from the settings menu it will show you which user id belongs to each process.

Also running the command "w" in a terminal window will show you who is logged in and where.

Thank you very much! When I run w, it shows me only a single session of my account, using xinitrc. 

```

USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
berker   tty8     :0               12:05    1:52m  8.41s  0.08s /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc


```

Also, showing UID's I can see only my own account name. What might have caused this and how do I solve this?
If relevant, I have Google Chrome Remote Desktop setup on this computer.

---

### Post by Toz on 2015-06-20
> **nonkreon said:**
> If relevant, I have Google Chrome Remote Desktop setup on this computer.
Yes, this is why. Google Chrome Remote Desktop will create a session for its own purposes and you will see duplicated processes in your process list.

---

### Post by nonkreon on 2015-06-20
> **Toz said:**
> Yes, this is why. Google Chrome Remote Desktop will create a session for its own purposes and you will see duplicated processes in your process list.

Well then, mystery solved. I thought I could come up with a way to clear RAM but that expected then :( 
Thank you very much, Toz.

---

