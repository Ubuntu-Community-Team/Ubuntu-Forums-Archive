---
title: "kbuildsycoca errors when logging in"
date: 2007-10-02
forum: Desktop Environments
---

### Post by antisho on 2007-10-02
GNOME crashes immediately after logging in, unless I don't press OK in the "Your session lasted less than 10 seconds" dialog. Said dialog lets me view .xsession_errors, which doesn't say anything about the source of the error. However, I logged into xfce and did a cat .xsession_errors, part of which gave me...

```
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
Traceback (most recent call last):
  File "/usr/bin/restricted-manager", line 404, in <module>
    sys.exit(main(args, opts))
  File "/usr/bin/restricted-manager", line 269, in main
    handlers = get_handlers()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/core.py", line 384, in get_handlers
    restricted = load_restricted_list()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/core.py", line 123, in load_restricted_list
    return generate_restricted_list(modules_dep, modules_restricted, force)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/core.py", line 146, in generate_restricted_list
    stdout=subprocess.PIPE, stderr=subprocess.PIPE)
  File "/usr/lib/python2.5/subprocess.py", line 593, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 13] Permission denied
checking for valid crashreport now
(synaptic:7961): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
xscreensaver: 22:42:19: 0: unrecognised ClientMessage "_NET_WM_STATE" received
xscreensaver: 22:42:19: 0: for window 0x3603cc9 (synaptic / Synaptic)
xscreensaver: 22:42:19: 0: unrecognised ClientMessage "_NET_WM_STATE" received
xscreensaver: 22:42:19: 0: for window 0x3603cc9 (synaptic / Synaptic)

(synaptic:7961): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
xscreensaver: 22:44:00: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 22:44:00: 0: for window 0x3600025 (synaptic / Synaptic)
xscreensaver: 22:44:25: 0: unrecognised ClientMessage "_NET_WM_STATE" received
xscreensaver: 22:44:25: 0: for window 0x3614b5d (synaptic / Synaptic)
```

Anyone know how to fix this? Thanks!

---

