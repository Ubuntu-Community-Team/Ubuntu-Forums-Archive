---
title: "Need Help..Accidently delete the panel"
date: 2011-02-01
forum: Desktop Environments
---

### Post by crownclown on 2011-02-01
Before this i got this panel at my desktop..then i accidently  del it...
how can i get back the panel 
now i only got no panel.
i use the kupfer to open any application ...so sad...
is there any way for me to get my panel back...
T.T
can someone help me...
Still new with ubuntu

---

### Post by Krytarik on 2011-02-01
Remove the directory "~/.gconf/apps/panel", this should restore the default panels:

- logout
- press Alt+Ctrl+F1
- login at the console
```
rm -rf .gconf/apps/panel
```- logout at the console
- press Alt+Ctrl+F8 or F7
- login again

---

### Post by crownclown on 2011-02-01
> **Krytarik said:**
> Remove the directory "~/.gconf/apps/panel", this should restore the default panels:

- logout
- press Alt+Ctrl+F1
- login at the console
```
rm -rf .gconf/apps/panel
```- logout at the console
- press Alt+Ctrl+F8 or F7
- login again


hey thanks man..it really works.....

---

### Post by Krytarik on 2011-02-01
Great! Then please mark this thread as "solved", via "Thread Tools".

---

