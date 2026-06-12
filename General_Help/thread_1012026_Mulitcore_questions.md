---
title: "Mulitcore questions"
date: 2008-12-15
forum: General Help
---

### Post by enigmamachine42 on 2008-12-15
Does anyone know how I can check and specify which core a process runs on?  Right now, it looks like everything only runs on one core, but I can't be sure. Thanks.

---

### Post by iponeverything on 2008-12-15
run 

```
htop
```

---

### Post by albandy on 2008-12-15
open a console and type top. 
You will see where the process are running. 
In the 2nd line you will see how many process are active, I've got a dual core, so top reports me that 2 process are running at the same time, if you've a quad core or more you will se as process running at the same time as cores have your machine.

Exist a bash command to select what processor runs a process but I dont remember it's name.

---

