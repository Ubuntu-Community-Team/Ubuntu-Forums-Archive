---
title: "Problem with nautilus..."
date: 2010-03-23
forum: Desktop Environments
---

### Post by Cosmos42 on 2010-03-23
So my places haven't been opening up when i click on them (documents, desktop, etc) and when I typed "nautilus" in the terminal, this is what I got:

nathansaccount@ubuntu:~$ nautilus

(nautilus:2051): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:2051): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2051): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2051): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Segmentation fault
nathansaccount@ubuntu:~$ 


Any ideas?

---

### Post by sxmaxchine on 2010-03-23
dont know how to fix your problem sorry but you can download dolphin as an alternative to nautilus

---

### Post by Yellow Pasque on 2010-03-23
I would go into Synaptic, search for nautilus, and mark the installed nautilus packages for reinstallation.

> but you can download dolphin as an alternative to nautilus
I would try Thunar (xfce's file manager) first. It uses a lot of the same gtk/gnome libs, whereas dolphin uses qt/kde libs and would require more stuff to be installed.

---

