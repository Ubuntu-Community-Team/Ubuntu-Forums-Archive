---
title: "gvim crashes when doing :Ex or :gdiff"
date: 2017-10-19
forum: Desktop Environments
---

### Post by dwater on 2017-10-19
I am suddenly getting gvim crash when doing certain things, though vim seems to work fine.

For example, if I run gvim on a directory, eg `gvim src/`, it would normally open with a directory listing, allowing me to navigate into a directory. Instead, the window pops open, then quickly closes again, with the following error message:
[INDENT](gvim:14290): GLib-CRITICAL **: g_ptr_array_insert: assertion 'index_ <= (gint)rarray->len' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14290): CRITICAL **: unity_gtk_menu_shell_get_item: assertion '0 <= index && index < items->len' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14290): CRITICAL **: unity_gtk_menu_item_get_child_shell: assertion 'UNITY_GTK_IS_MENU_ITEM (item)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14290): CRITICAL **: unity_gtk_menu_shell_get_item: assertion '0 <= index && index < items->len' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14290): CRITICAL **: unity_gtk_menu_item_get_label: assertion 'UNITY_GTK_IS_MENU_ITEM (item)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14290): CRITICAL **: unity_gtk_menu_item_get_icon: assertion 'UNITY_GTK_IS_MENU_ITEM (item)' failed[/INDENT]
[INDENT]Vim: Caught deadly signal SEGV[/INDENT]
[INDENT]Vim: Finished.[/INDENT]

I can open gvim without any file, or by specifying a file, and it seems to work fine. If I then do ':Ex', then it crashes again, with:
[INDENT](gvim:14405): GLib-CRITICAL **: g_ptr_array_insert: assertion 'index_ <= (gint)rarray->len' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14405): CRITICAL **: unity_gtk_menu_shell_get_item: assertion '0 <= index && index < items->len' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14405): CRITICAL **: unity_gtk_menu_item_get_child_shell: assertion 'UNITY_GTK_IS_MENU_ITEM (item)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14405): CRITICAL **: unity_gtk_menu_shell_get_item: assertion '0 <= index && index < items->len' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14405): CRITICAL **: unity_gtk_menu_item_get_label: assertion 'UNITY_GTK_IS_MENU_ITEM (item)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14405): CRITICAL **: unity_gtk_menu_item_get_icon: assertion 'UNITY_GTK_IS_MENU_ITEM (item)' failed[/INDENT]
[INDENT]Vim: Caught deadly signal SEGV[/INDENT]
[INDENT]Vim: Finished.[/INDENT]


Similarly, if I try to do a 'Gdiff':
[INDENT](gvim:14495): GLib-CRITICAL **: g_ptr_array_insert: assertion 'index_ <= (gint)rarray->len' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14495): CRITICAL **: unity_gtk_menu_shell_get_item: assertion '0 <= index && index < items->len' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14495): CRITICAL **: unity_gtk_menu_item_get_child_shell: assertion 'UNITY_GTK_IS_MENU_ITEM (item)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14495): CRITICAL **: unity_gtk_menu_shell_get_item: assertion '0 <= index && index < items->len' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14495): CRITICAL **: unity_gtk_menu_item_get_label: assertion 'UNITY_GTK_IS_MENU_ITEM (item)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (gvim:14495): CRITICAL **: unity_gtk_menu_item_get_icon: assertion 'UNITY_GTK_IS_MENU_ITEM (item)' failed[/INDENT]
[INDENT]Vim: Caught deadly signal SEGV[/INDENT]
[INDENT]Vim: Finished.[/INDENT]

Using 17:04 with :
[INDENT]$ dpkg -l | grep vim[/INDENT]
[INDENT]ii  vim                                             2:8.0.0095-1ubuntu3                                     amd64        Vi IMproved - enhanced vi editor[/INDENT]
[INDENT]ii  vim-common                                      2:8.0.0095-1ubuntu3                                     all          Vi IMproved - Common files[/INDENT]
[INDENT]ii  vim-gnome                                       2:8.0.0095-1ubuntu3                                     all          Vi IMproved - enhanced vi editor (dummy package)[/INDENT]
[INDENT]ii  vim-gtk3                                        2:8.0.0095-1ubuntu3                                     amd64        Vi IMproved - enhanced vi editor - with GTK3 GUI[/INDENT]
[INDENT]ii  vim-gui-common                                  2:8.0.0095-1ubuntu3                                     all          Vi IMproved - Common GUI files[/INDENT]
[INDENT]ii  vim-runtime                                     2:8.0.0095-1ubuntu3                                     all          Vi IMproved - Runtime files[/INDENT]
[INDENT]ii  vim-tiny                                        2:8.0.0095-1ubuntu3                                     amd64        Vi IMproved - enhanced vi editor - compact version[/INDENT]

Only recent changes are an attempt to install drivers for logitech, which required me to do `sudo dpkg --add-architecture i386`...though I never actually managed to get them installed.

Any ideas/suggestions?

---

