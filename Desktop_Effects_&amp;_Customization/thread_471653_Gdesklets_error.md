---
title: "Gdesklets error"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by Nirva on 2007-06-12
Hay,

I have a problem with gdesklets.  It used to work, but 2 weeks ago, I switched to beryl and back again, and ever since, there is this problem.
I can start gdesklets, but when I ask to open the shell, i get this error.  Does anyone have an idea?

filip@filip:~$ gdesklets shell
filip@filip:~$ ./Shell/__init__.py:153: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[06/12/07-14:24:05]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]GtkCheckMenuItem.__init__() argument 1 must be string without null bytes or None, not str
in /usr/lib/gdesklets/gdesklets-shell: line 9 <module>
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 52 get_plugin
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 40 get_plugins_by_pattern
in ./Shell/__init__.py: line 70 init
in /usr/lib/gdesklets/shell/Plugin.py: line 18 _get_plugins_by_pattern
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 40 get_plugins_by_pattern
in ./Profiles/__init__.py: line 24 init
in ./Profiles/__init__.py: line 39 __build_menu
in ./Menu/__init__.py: line 163 set_check_item
[EXC]/usr/lib/gdesklets/shell/plugins/Menu/__init__.py

[---]  158     #
[---]  159     # Sets the given node to be a checkbox menu item.
[---]  160     #
[---]  161     def set_check_item(self, path, label, callback, *args):
[---]  162 
[ERR]> 163         item = gtk.CheckMenuItem(label)
[---]  164         item.show()
[---]  165         if (callback):
[---]  166             def f(*nil): callback(*args)
[---]  167             item.connect("activate", f)
[---]  168 
[---]  169         return self.__set_node(path, item)

---

### Post by timcredible on 2007-06-12
i've found that beryl and gdesklets don't really like each other.  it's probably easiet to just remove gdesklets via synaptic and then reinstall it.

---

### Post by Nirva on 2007-06-12
I've already done that.  I even tried reinstalling gdesklets and gdesklets data

---

