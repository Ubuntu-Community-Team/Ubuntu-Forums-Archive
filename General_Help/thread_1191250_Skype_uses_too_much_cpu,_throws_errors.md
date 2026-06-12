---
title: "Skype uses too much cpu, throws errors"
date: 2009-06-18
forum: General Help
---

### Post by cwgpress on 2009-06-18
I've got latest everything but still having problems. Only using the chat part.

64-bit Ubuntu, 64-bit Skype.
When started from menu Skype is unkillable (quit on notification icon is ignored, kill with pid is ignored) and it takes 70% of cpu.

When started from command line:
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
ALSA lib ../../../src/pcm/pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
...lots of the ALSA messages...
RtApiAlsa: underrun detected.
...underrun message thrown occasionally...

Any ideas appreciated.

---

