---
title: "How to stop using compiz fusion"
date: 2007-12-05
forum: Desktop Environments
---

### Post by ndefontenay on 2007-12-05
Hi.

I use Kubuntu Gutsy.

I've installed Compiz Fusion recently.
It looks really nice and all but is really resource demanding.
I would like to be able to turn it off when I don't want to use it.
How can I just disable compiz fusion and enable it later when I want it?

Thanks in advance.

Nico

---

### Post by staticvoid on 2007-12-05
run this command, hit Alt F2
```
kwin --replace
```

that will replace whatever windows manager you currently have running with kwin (KDE's manager)

I do metacity --replace in gnome


sv

---

### Post by Znort_Ubern00b on 2007-12-05
create launchers on your desktop

right click on desktop add launcher
call one **compiz start** and add command
compiz --replace
and the other
**compiz stop** and add command 
kwin --replace

saves opening terminal to do it.

---

### Post by staticvoid on 2007-12-05
but can't you just do alt f2?

i dunno... idon't like filling my desktop up with icons...

---

