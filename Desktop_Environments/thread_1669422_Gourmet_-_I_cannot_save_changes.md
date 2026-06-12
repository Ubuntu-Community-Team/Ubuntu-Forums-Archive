---
title: "Gourmet - I cannot save changes"
date: 2011-01-17
forum: Desktop Environments
---

### Post by vasicekabc on 2011-01-17
Using Gourmet recipe manager I cannot save changes. Everything look well if I edit recipe, but every changes in recipes, which I did are lost. I can create new recipe, its OK. But cannot make changes. I think something is missing in my system, but I cannot understand terminal:

```
vasek@notes:~$ gourmet														# Here
/usr/local/lib/python2.6/dist-packages/gourmet/gtk_extras/mnemonic_manager.py:312: GtkWarning: Invalid input string		# the program Gourmet
 *widget.set_text_with_mnemonic(txt[0:index] + '_' + txt[index:])								# starts
/usr/local/lib/python2.6/dist-packages/gourmet/GourmetRecipeManager.py:1012: GtkWarning: Invalid input string		
 *self.main.add(self.main_notebook)											#-------------------------------------
/usr/local/lib/python2.6/dist-packages/gourmet/reccard.py:951: GtkWarning: UnitConverter: missing action UnitConverter
 *main_vb.pack_start(self.ui_manager.get_widget('/RecipeEditorMenuBar'),expand=False,fill=False)				# Here
/usr/local/lib/python2.6/dist-packages/gourmet/reccard.py:951: GtkWarning: Undo: missing action Undo				# is edit window
 *main_vb.pack_start(self.ui_manager.get_widget('/RecipeEditorMenuBar'),expand=False,fill=False)				# opening
/usr/local/lib/python2.6/dist-packages/gourmet/reccard.py:951: GtkWarning: Redo: missing action Redo
 *main_vb.pack_start(self.ui_manager.get_widget('/RecipeEditorMenuBar'),expand=False,fill=False)
/usr/local/lib/python2.6/dist-packages/gourmet/GourmetRecipeManager.py:726: GtkWarning: Cut: missing action Cut
 *gtk.main()
/usr/local/lib/python2.6/dist-packages/gourmet/GourmetRecipeManager.py:726: GtkWarning: Copy: missing action Copy
 *gtk.main()
/usr/local/lib/python2.6/dist-packages/gourmet/GourmetRecipeManager.py:726: GtkWarning: Paste: missing action Paste
 *gtk.main()														#-------------------------------------
Traceback (most recent call last):								
 *File "/usr/local/lib/python2.6/dist-packages/gourmet/reccard.py", line 1021, in save_cb					# Here
 * *newdict = m.save(newdict)													# I chosed
 *File "/usr/local/lib/python2.6/dist-packages/gourmet/reccard.py", line 1222, in save						# "save"
 * *self.ingtree_ui.ingController.commit_ingredients()
 *File "/usr/local/lib/python2.6/dist-packages/gourmet/reccard.py", line 2120, in commit_ingredients
 * *n = commit_iter(iter,n)
 *File "/usr/local/lib/python2.6/dist-packages/gourmet/reccard.py", line 2091, in commit_iter
 * *if getattr(ing,att)==d[att]: del d[att]
KeyError: 'ingkey'

```

---

