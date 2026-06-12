---
title: "beryl-settings broken"
date: 2007-02-13
forum: Desktop Environments
---

### Post by android6011 on 2007-02-13
I fixed the beryl-settings and changed "python" to "python2.5" to get it to load and now I get:

/usr/bin/beryl-settings:22: RuntimeWarning: Python C API version mismatch for module berylsettings: This Python has API version 1013, module berylsettings has version 1012.
  import berylsettings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 1949, in <module>
    MakeCategoryArea(Category)
  File "/usr/bin/beryl-settings", line 1788, in MakeCategoryArea
    PlugInfo = MakePluginArea(Plugin)
  File "/usr/bin/beryl-settings", line 1691, in MakePluginArea
    MakeGroupArea(Group,NoteBook)
  File "/usr/bin/beryl-settings", line 1624, in MakeGroupArea
    if (MakeSubGroupArea(SubGroup,VBox)):
  File "/usr/bin/beryl-settings", line 1569, in MakeSubGroupArea
    GroupVBox.pack_start(MakeBackendWidgets(),True,True)
  File "/usr/bin/beryl-settings", line 1507, in MakeBackendWidgets
    for backend in berylsettings.Backends():
AttributeError: 'module' object has no attribute 'Backends'

---

