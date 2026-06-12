---
title: "kill connection"
date: 2006-01-06
forum: General Help
---

### Post by Ocxic on 2006-01-06
i have a few connections in firestarter i do not want to be there, how do i kill those connections?

---

### Post by bagel on 2006-01-06
hmm.. I believe the easiest way would be to stop the corresponding programs/services? But maybe I'm overlooking something?

Ciao, bagel

---

### Post by Ocxic on 2006-01-06
the service in gnutella but i am not running anything that uses that, and now firtestarter can't find my preferences file!?!?

---

### Post by bagel on 2006-01-06
Hello;

I believe there might be some way to map a connection to a program?!
```

netstat -a --tcp -e

```
will give you at least the user running the process.

I would also have a look if
```
chkrootkit
```
finds something(just to make sure)

Ciao, bagel

---

### Post by s_spiff on 2006-01-06
hey everytime I boot up , I have to start the connection by typing in the terminal the following :
pon dsl-provider 

and kill the connection by 

poff dsl-provider

Is there some script or something that I can do, so that when I log in , it automatically connects, that is, this command is automatically passed to the system, and I don't have to sit and type this out?

---

