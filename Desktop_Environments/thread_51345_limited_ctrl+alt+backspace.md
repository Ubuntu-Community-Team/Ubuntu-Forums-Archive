---
title: "limited ctrl+alt+backspace?"
date: 2005-07-23
forum: Desktop Environments
---

### Post by fabiuu on 2005-07-23
why can i ctrl+alt+backspace only like 3 times per boot?

on the last one, instead of restarting the X I get the login on the black screen and nothing else  :-? 

thanks in advance

---

### Post by ritger on 2005-07-23
*I think* GDM (the graphical login manager) keeps track on how many times the X server `crashes' (using ctrl+alt+backspace is not a clean way to close the X server). You can always restart GDM by logging in on the regular boot and typing:
```
sudo /etc/init.d/gdm restart && exit
```

---

