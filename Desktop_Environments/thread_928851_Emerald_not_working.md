---
title: "Emerald not working"
date: 2008-09-24
forum: Desktop Environments
---

### Post by Killtodie on 2008-09-24
I just installed emerald and its not accepting a new theme. Had the same problem before but I cant remember what the solutions was.

Cant find it in search either.

---

### Post by anotherdisciple on 2008-09-24
It it enabled.... open a terminal (Applications > Accessories > Terminal)

and type:

```
emerald --replace &
```

---

### Post by Killtodie on 2008-09-24
yes, thats the command. but i remember doing it under sessions I think..

---

### Post by Jeggred on 2008-09-24
If you want emerald to run at startup go to System>Preferences>Sessions and on the Startup Programs tab press the Add button. Now in the command textbox type ```
emerald --replace &
``` and name it whatever you want this will enable it at startup.

---

### Post by anotherdisciple on 2008-09-25
> **Jeggred said:**
> If you want emerald to run at startup go to System>Preferences>Sessions and on the Startup Programs tab press the Add button. Now in the command textbox type ```
emerald --replace &
``` and name it whatever you want this will enable it at startup.

You can do that... but in my experience... it stays consistent even when I don't put it in my sessions... is this not the case with you?

---

### Post by Theo148 on 2008-09-25
If you're running Compiz and you have CCSM installed, you could just set the command for the 'Window Decoration' plugin to 'emerald --replace'. :)

---

