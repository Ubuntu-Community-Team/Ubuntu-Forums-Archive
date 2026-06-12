---
title: "Problem installing gDesklets"
date: 2006-01-05
forum: General Help
---

### Post by luison9999 on 2006-01-05
Hi
Y downloaded gDesklets from synaptic(apt-get) and it installed without deps errors.
But when I try to run, I receive this message:

Parse Error: <unknown>:1:0: syntax error
Traceback (most recent call last):
  File "/usr/bin/gdesklets", line 76, in ?
    starter.start_displays()
  File "/usr/share/gdesklets/main/Starter.py", line 251, in start_displays
    self.__on_watch(None, None)
  File "/usr/share/gdesklets/main/Starter.py", line 89, in __on_watch
    self.__add_display(ident, displays[ident])
  File "/usr/share/gdesklets/main/Starter.py", line 116, in __add_display
    dsp = self.__create_display(ident, path)
  File "/usr/share/gdesklets/main/Starter.py", line 171, in __create_display
    _("The display file contains invalid data and "
  File "/usr/share/gdesklets/utils/dialog.py", line 39, in warning
    _set_message(dialog, primary, secondary)
  File "/usr/share/gdesklets/utils/dialog.py", line 21, in _set_message
    lbl.set_markup(message)
AttributeError: 'gtk.VBox' object has no attribute 'set_markup'

---

