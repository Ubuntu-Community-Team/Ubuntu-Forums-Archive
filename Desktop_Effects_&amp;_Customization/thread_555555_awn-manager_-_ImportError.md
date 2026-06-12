---
title: "awn-manager - ImportError"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by HokeyFry on 2007-09-20
i just installed the avant window navigator and when i try to open the awm-manager i get this error

```
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 40, in <module>
    import gnomedesktop
ImportError: No module named gnomedesktop

```

any ideas? i know what the error means, i just dont know how to fix it :confused:

---

### Post by HokeyFry on 2007-09-20
i ended up fixing it, i had to install the following 3 packages

```
python-gnome2-desktop
python-gnome2
python-gnome2-extras
```

these packages should be provided by default so use apt-get, synaptic, or whatever floats your boat


hab spass

---

### Post by HokeyFry on 2007-09-20
nvm its not fixed, when i try to add a launcher i get this error, but the program doesnt crash:

```
File "/usr/lib/python2.5/subprocess.py", line 593, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```


i am working on trying to fix this, and ill post if i do, but if anyone knows what to do please by all means

---

### Post by HokeyFry on 2007-09-26
anyone?


i think that the problem is that awn-manager is not finding this file

/usr/lib/python2.5/subprocess.py


any ideas? please? im sure im not the only one with this problem :(

---

