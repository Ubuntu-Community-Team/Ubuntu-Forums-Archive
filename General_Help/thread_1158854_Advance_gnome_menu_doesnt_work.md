---
title: "Advance gnome menu doesnt work"
date: 2009-05-14
forum: General Help
---

### Post by knox.no on 2009-05-14
hi,
i've installed agm from [http://www.sciallo.net](http://www.sciallo.net). 
i tried first agm_0.8.3-2_all.deb but it didnt show me the list of menus,
so i downloaded the svn version but it didnt work.

> 
Running installed agm, modifying PYTHONPATH.
Running installed agm, modifying PYTHONPATH.
[]
/usr/local/lib/python/AGM/AGM_Navigation_Button.py:24: GtkWarning: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
  button.realize()
0 0
Attribute Error  ConfigureBrowseFiles 'module' object has no attribute 'Plugin'
Attribute Error  Home 'module' object has no attribute 'Plugin'
[]
Traceback (most recent call last):
  File "./AGM.py", line 103, in <module>
    AGM(top_buttons=False)
  File "/usr/local/lib/python/AGM/AGM_Main_Window.py", line 110, in __init__
    self.setObjects();
  File "/usr/local/lib/python/AGM/AGM_Main_Window.py", line 397, in setObjects
    self.execution_box=ExecuteBar(self.win.get_gradient)
  File "/usr/local/lib/python/AGM/AGM_execute_box.py", line 40, in __init__
    self.label=gtk.Label(_("Execute")+ ":")
  File "/usr/local/lib/python/AGM/localization.py", line 32, in Translate
    return unicode( gettext.gettext(string), "utf-8" )
  File "/usr/lib/python2.6/gettext.py", line 581, in gettext
    return dgettext(_current_domain, message)
  File "/usr/lib/python2.6/gettext.py", line 545, in dgettext
    codeset=_localecodesets.get(domain))
  File "/usr/lib/python2.6/gettext.py", line 493, in translation
    t = _translations.setdefault(key, class_(open(mofile, 'rb')))
  File "/usr/lib/python2.6/gettext.py", line 180, in __init__
    self._parse(fp)
  File "/usr/lib/python2.6/gettext.py", line 314, in _parse
    plural = v[1].split('plural=')[1]
IndexError: list index out of range



iam with ubuntu jaunty.

---

