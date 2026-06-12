---
title: "HARDY: Can't install new languages using gnome-language-selector"
date: 2008-02-15
forum: Desktop Environments
---

### Post by magicfab on 2008-02-15
Using a clean install of Hardy I can't seem to install new languages support via System > Administration > Language Support or command line using sudo gnome-language-selector.

When I go via the menus, I can choose the language, hit OK andnothing happens then.

Here is the output I get from command line:

```
magicfab@diana:~$ sudo gnome-language-selector 
[sudo] password for magicfab: 
/usr/lib/python2.5/site-packages/LanguageSelector/gtk/GtkLanguageSelector.py:559: 
GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
* Reloading GNOME Display Manager configuration...                              
* Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
magicfab@diana:~$ man gnome-language-selector
No manual entry for gnome-language-selector
See 'man 7 undocumented' for help when manual pages are not available.
magicfab@diana:~$
```

I am waiting to file a bug, if anyone could confirm this, I am bit surprised I don't see any references to such an obvious problem.

Thanks!

---

