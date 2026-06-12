---
title: "Mistake using Compix"
date: 2007-02-21
forum: Desktop Environments
---

### Post by Billy McCann on 2007-02-21
Hi y'all.  

I think I've made a mistake using compix.  I installed it and activated it using the command 
```
compiz --replace gconf
```
My desktop started acting somewhat shaky and crashed.  So I uninstalled compix.   

I think this was a mistake.  How can I get gnome as it was before I ran the replace command?

Thanks.

Billy

---

### Post by louis_nichols on 2007-02-21
You open a terminal window in gnome and use the command:

```
metacity --replace 
```

This will start the default gnome window manager. Then you can close the terminal window. Metacity will be killed when you do this, but it will start again on its own.

---

### Post by Billy McCann on 2007-02-21
Thanks Louis.

---

