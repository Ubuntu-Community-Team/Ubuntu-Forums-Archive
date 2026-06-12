---
title: "CompizFusion showing black windows and menus, how to disable it?"
date: 2009-11-19
forum: Desktop Environments
---

### Post by SlaughterDog on 2009-11-19
So I turned on the 'burry windows' effect for CompizFusion on Ubuntu 9.04. Now, windows and menus just render black. Well just about everything does, and leaves a black box on the screen. 

How do I disable this when I can't see anything in the GUI?

Perhaps I can start it up with Metacity, then use CCSM to disable the effects? 

Or will I need to edit a conf file to turn it off?

---

### Post by gettinoriginal on 2009-11-19
This should help you.  Open in Metacity, then open a terminal and enter the following code.  It should reset compiz to default settinigs.
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by SlaughterDog on 2009-11-19
How do I open in Metacity though?

Edit: nevermind, just ran the command on tty. Thanks!

---

### Post by gettinoriginal on 2009-11-20
Can you open and see a terminal from applications??  If so, enter
```
metacity --replace
```

Also, install compiz fusion icon, then add it to your panel, it allows instant ability to switch window managers and window decorators.  I use it when I mess up my settings in compiz.

---

