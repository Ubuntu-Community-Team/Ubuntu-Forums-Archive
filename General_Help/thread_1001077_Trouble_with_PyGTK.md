---
title: "Trouble with PyGTK"
date: 2008-12-03
forum: General Help
---

### Post by vmaaxt on 2008-12-03
None of my programs realise that I have PyGTK installed

```
alex@alex-laptop:~$ comix
PyGTK version 2.8.0 or higher is required to run Comix.
No version of PyGTK was found on your system.

```

Rhythmbox yields a segmentation fault.

```
(15:49:54) [0x80dc028] [rb_plugins_engine_load] rb-plugins-engine.c:108: Loading plugin: /usr/lib/rhythmbox/plugins/lyrics/lyrics.rb-plugin
(15:49:54) [0x80dc028] [rb_plugins_engine_load] rb-plugins-engine.c:198: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/lyrics/lyrics.rb-plugin
(15:49:54) [0x80dc028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:291: Plugin Song Lyrics loaded
(15:49:54) [0x80dc028] [rb_python_module_init] rb-python-module.c:387: Init of python module
Segmentation fault

```

But I have python-gtk2 installed

```
alex@alex-laptop:~$ sudo apt-get install python-gtk2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gtk2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I'm afraid I might have broken something horribly. I installed Python from source, before I realized I already had it.

Please help! Thanks in advance.

---

