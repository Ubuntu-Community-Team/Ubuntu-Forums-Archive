---
title: "Compiz cube problems"
date: 2011-01-16
forum: Desktop Environments
---

### Post by a_b_b_ on 2011-01-16
I am using Ubuntu 10.04. Initially Compiz cube used to run well. However after running the update manager Compiz has stopped running. I tried running it through terminal but this is the message i get:

[I]Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
[/I]

Any help guys?

---

### Post by a_b_b_ on 2011-01-16
Also running compiz-check has the following output

Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by Forlong on 2011-01-31
Did you manage to solve this?
If not, please post the ouput of
```
dpkg -l | grep "nvidia\|fglrx"
```

---

### Post by a_b_b_ on 2011-02-03
Miraculously the problem resolved itself somehow! :D
I think it was primarily related to some update because the problem started after i completed an update. 
Anyway i was trying out the effects using 'Visual effects' and chose 'Extra'. Ubuntu then searched for new drivers (something that hadn't happened previously) and just like that everything was back to normal!

---

