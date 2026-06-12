---
title: "How do I set the default desktop manager from shell"
date: 2009-03-27
forum: Desktop Environments
---

### Post by edweird13 on 2009-03-27
I set Compiz as my default desktop manager and when I start up I get a blank black screen. How do I set metacity as my default desktop manager from a shell without a xsession started?

---

### Post by UbuntuNerd on 2009-03-27
try this command  
```
killall compiz && metacity --replace
```

---

### Post by edweird13 on 2009-03-27
no go I am in safe mode so xsession isn't loaded. If I try to boot with X the machine basicly stops responding can't get to a login prompt GUI or command line. There has to be a config file somewhere I can edit.

---

### Post by edweird13 on 2009-03-28
bunp. Is there a problem with the new X update? if so I will wait for 9.04

---

