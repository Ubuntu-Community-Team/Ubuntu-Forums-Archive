---
title: "Alacarte menu editor not working in Dapper"
date: 2006-10-25
forum: Desktop Environments
---

### Post by mattalves on 2006-10-25
Heypa people, I'm having a bit of trouble now with the alacarte menu editor. It simply won't start in my Dapper installation. Any clues what to check, what to fix?

Thanks and cheers,

Mateus

---

### Post by rimbaud on 2006-10-29
I am using Edgy and it won't start from the menus. When I run it from the command line, it loads OK but won't let me make any changes and spits out unpleasant stuff in the shell like:

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 441, in on_menu_contents_changed
    self.saveMenu(self.menu_original_values, True)
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 463, in saveMenu
    if path == values[0]:
IndexError: tuple index out of range
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 441, in on_menu_contents_changed
    self.saveMenu(self.menu_original_values, True)
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 463, in saveMenu
    if path == values[0]:
IndexError: tuple index out of range

---

### Post by rimbaud on 2006-10-30
OK, it now works.  It still spits out unpleasant messages like above, but not being able to change the menu items was a permissions problem relating to me restoring an old backup.  Changing the ownership of the relevant files (it tells you which in the console) now means the menu editor works perfectly.

Suggestion: it might be good if the menu editor complains if it doesn't have permissions.

---

