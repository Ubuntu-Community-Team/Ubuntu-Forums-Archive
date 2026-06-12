---
title: "Devilspie: how to NOT apply to existing?"
date: 2010-01-26
forum: Desktop Environments
---

### Post by Denis.Gorbachev on 2010-01-26
Hello everybody,

What I want is to hide all new Firefox windows opened *after* I've launched devilspie. However, when I launch devilspie, it will hide both new and *existing *windows.

What I already have is:

[LIST]
[*]No devilspie in Startup Applications (so that my first FF window does get opened as usual).
[*]No --apply-to-existing in devilspie args.
[*]A working rule to hide all Firefox windows.
[/LIST]

Ubuntu 9.04, devilspie 0.22-1

---

### Post by zlatkart on 2010-01-26
maybe you could try to change the window title of your firefox window with eg wmctrl

---

### Post by Denis.Gorbachev on 2010-01-27
No, I can't do that. I need to intercept Firefox at startup and hide it, not change its window title.

---

### Post by zlatkart on 2010-01-27
you could change the window title of your EXISTING Firefox window, so it wont be affected when (if 
       (is (window_name) "Firefox")

---

### Post by Denis.Gorbachev on 2010-01-29
Whoa. That seems to do the trick. Thank you!

---

