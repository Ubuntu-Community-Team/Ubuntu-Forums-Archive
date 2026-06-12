---
title: "menu-editor error"
date: 2005-05-03
forum: Desktop Environments
---

### Post by vegetto on 2005-05-03
I am getting this when i save an entry using menu-editor
> Traceback (most recent call last):
  File "/usr/bin/menu-editor", line 370, in saveEntry
    self.menu_handler.saveEntry(entry, name, comment, command, icon, useterm, category, filename)
  File "/usr/lib/menu-editor/menu_handler.py", line 130, in saveEntry
    if newentry.content['Desktop Entry'].has_key('Name[' + self.locale + ']'):
TypeError: cannot concatenate 'str' and 'NoneType' objects 

tried as root also, i think there is some programming error in python file. can anyone give me a pointer.

---

