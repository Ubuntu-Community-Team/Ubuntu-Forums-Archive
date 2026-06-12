---
title: "dependency error"
date: 2008-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pibb69173 on 2008-12-11
i keep trying to update but when i try to start the manager either in terminal or Via GUI it crashes here is the output from the terminal
```


agent@agent-laptop:~$ synaptic update manager

** (synaptic:6222): CRITICAL **: failed to load icon 'lpi-help': Icon 'lpi-help' not present in theme

(synaptic:6222): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

** (synaptic:6222): CRITICAL **: failed to load icon 'lpi-translate': Icon 'lpi-help' not present in theme

(synaptic:6222): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

** (synaptic:6222): CRITICAL **: failed to load icon 'lpi-bug': Icon 'lpi-help' not present in theme
Bus error
agent@agent-laptop:~$ Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 511, in <module>
    lockfd = os.open(XAPIANDBLOCK, os.O_RDWR | os.O_CREAT)
OSError: [Errno 13] Permission denied: '/var/lib/apt-xapian-index/update-lock'

agent@agent-laptop:~$ 


```

---

### Post by pibb69173 on 2008-12-11
Also none other type of package manager or program installer will open much help needed and apreciated

---

