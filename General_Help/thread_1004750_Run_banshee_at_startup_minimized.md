---
title: "Run banshee at startup minimized"
date: 2008-12-07
forum: General Help
---

### Post by munit5000 on 2008-12-07
Hey, I know how to run banshee at startup by using the sessions manager, but does anyone know how to run banshee minimized to the tray at startup?

---

### Post by jmoorse on 2008-12-07
I would try appending -hide to the end of your session command.  I am not sure if this will achieve your goal but it is the closest switch the version I use supports


--Jeff Moorse

---

### Post by munit5000 on 2008-12-07
Well if I try typing 

```

banshee -hide

```

into the terminal right now it stays maximized when it starts :-k

---

### Post by Paulpro on 2011-03-23
You probably figured this out, but this was the top result when I googled for this. So, for anyone else, it should be:

```
banshee --hide
```

---

