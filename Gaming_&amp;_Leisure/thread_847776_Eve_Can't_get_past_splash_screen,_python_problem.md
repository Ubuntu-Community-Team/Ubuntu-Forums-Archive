---
title: "Eve: Can't get past splash screen, python problem?"
date: 2008-07-02
forum: Gaming &amp; Leisure
---

### Post by Paul Brando on 2008-07-02
Eve-online pops up a splash screen, but then crashes. The console says: 


```
Single-user install...
This is the update checker... 
Running /home/paul/.cedega/.updater/cedega_updater.py
/home/paul/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Running... /home/paul/.cedega/.ui/runGUI
/home/paul/.cedega/.ui/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
paul@gateway:~$ X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  146 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3565
  Current serial number in output stream:  3567
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  62 (X_CopyArea)
  Resource id in failed request:  0x3c0034e
  Serial number of failed request:  3570
  Current serial number in output stream:  3571

```

Any ideas?

---

### Post by Cappy on 2008-07-02
Try
```
mv ~/.cedega ~/.cedega.bak
```

Also post your video card and the output of
```
glxinfo | grep 'OpenGL\|direct'
```
(by copying and pasting that into the terminal)

---

### Post by rbarbe on 2008-08-07
I have the same problem, I did what you recomend, here it is the output

```


roberto@ORION:~$ mv ~/.cedega ~/.cedega.bak
roberto@ORION:~$ glxinfo | grep 'OpenGL\|direct'
direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX 440 with AGP8X/AGP/SSE/3DNOW!
OpenGL version string: 1.5.8 NVIDIA 96.43.05
OpenGL extensions:
roberto@ORION:~$ 

```:

---

