---
title: "Printer admin won't launch (gtk.glade?)"
date: 2009-06-16
forum: General Help
---

### Post by ThinkBuntu on 2009-06-16
For some reason, my machine is not seeing the printer on our local network. I cannot even launch the "Printer" helper (/usr/bin/system-config-printer), which produces the following traceback:

```
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 29, in <module>
    import gtk.glade
ImportError: No module named gtk.glade
```

I have the "python-glade2" package installed, so I'm not sure what package would fix this problem. Also, "import gtk" fails in Python.

---

### Post by ThinkBuntu on 2009-06-16
Solved the problem. The user on this machine before me had built their own Python which had the wrong path.

---

