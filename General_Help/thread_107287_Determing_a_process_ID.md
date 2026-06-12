---
title: "Determing a process ID"
date: 2005-12-22
forum: General Help
---

### Post by Granduke on 2005-12-22
I am trying to setup SWAT and I'm stuck at this instruction:

"...you need to send a HUP signal to inetd. To do this use kill -1 PID  where PID is the process ID of the inetd daemon."

How do I determine what this process ID is?

---

### Post by kabus on 2005-12-22
In a terminal enter :

```
pidof inetd
```

---

### Post by Granduke on 2005-12-22
thanks kabus

---

