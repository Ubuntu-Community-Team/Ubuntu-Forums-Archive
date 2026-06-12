---
title: "Feisty 20070115 --amd64 Desktop CD (cannot install)"
date: 2007-01-15
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-01-15
Test case type: Feisty, Daily-live Desktop CD, installation
Image ID: 20070115 & 20070114
Date of testing: 20070115
md5sum confirmed: yes
Pass/Fail: Fail
Bugs identified:
Other comments: Both CDs checked for defects from CD boot menu. Both CDs boot OK, but for both installation does not work. The same happens when installing as guests in VMware 5.5.3. Log for both from terminal (did not know in which system log to locate the errors) is identical and as follows:

```
root@ubuntu:/home/ubuntu# ubiquity --desktop %k gtkui
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 185, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 180, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 44, in install
    mod = __import__('ubiquity.frontend', globals(), locals(), frontends)
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 53, in <module>
    from ubiquity.debconfcommunicator import DebconfCommunicator
  File "/usr/lib/ubiquity/ubiquity/debconfcommunicator.py", line 22, in <module>
    import debconf
ImportError: No module named debconf
root@ubuntu:/home/ubuntu#
```

---

### Post by pochu on 2007-01-15
Have you reported it on Lauchpad?

If you haven't done it, please, do it (but first search if it has already been done).

Thank you
Pochu

---

