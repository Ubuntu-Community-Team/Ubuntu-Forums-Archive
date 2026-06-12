---
title: "gDesklet crashes on startup"
date: 2006-08-23
forum: Desktop Environments
---

### Post by MyBigToe on 2006-08-23
I hope this is the right place to ask for help, ive seen other gdesklet threads here.

When i run gDesklets (with the command 'gDesklets shell') it opens, but then closes pretty much instantly,

using the terminal, it gives me this error:
```
andrew@andrew-desktop:~$ gdesklets shell
andrew@andrew-desktop:~$ glibtop: This machine has 1 CPUs, 1 are being monitored.

==========================================================[08/23/06-23:08:28]====== Unhandled error! Something bad and unexpected happened. ===

[EXC]list index out of range
in /usr/lib/gdesklets/gdesklets-shell: line 9 ?
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 52 get_plugin
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 40 get_plugins_by_pattern
in ./Shell/__init__.py: line 70 init
in /usr/lib/gdesklets/shell/Plugin.py: line 18 _get_plugins_by_pattern
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 40 get_plugins_by_pattern
in ./Profiles/__init__.py: line 24 init
in ./Profiles/__init__.py: line 39 __build_menu
in ./Menu/__init__.py: line 169 set_check_item
in ./Menu/__init__.py: line 79 __set_node
[EXC]/usr/lib/gdesklets/shell/plugins/Menu/__init__.py

[---]   74             if (not submenu):
[---]   75                 submenu = gtk.Menu()
[---]   76                 pitem.set_submenu(submenu)
[---]   77
[---]   78         parent, index = self.__get_node(path)
[ERR]>  79         name, nil, children = parent[index]
[---]   80         parent[index] = (name, item, children)
[---]   81         submenu.insert(item, index)
[---]   82
[---]   83
[---]   84
[---]   85     #




```

Can anyone help me please?

---

