---
title: "Perm unhide hidden folders?"
date: 2009-01-05
forum: Desktop Environments
---

### Post by silverbullet007 on 2009-01-05
I tried searching but probably didnt use the correct descriptor words..  Anyway instead of always having to hit ctrl+h or unhide them thru the menu.. is there a way to unhide all hidden folders.. or even just hidden but non-system folders/files permenantly?

---

### Post by mcduck on 2009-01-06
In Gnome? Open Nautilus, go to Edit/Preferences, and on the Views-tab enable the "Show hidden and backup files"-option.

---

### Post by silverbullet007 on 2009-01-07
Oh yes.. left out that tidbit of info.. Gnomes yes.  Thanks for the reply!  However is there a way to perform this in the command-line?

---

### Post by mcduck on 2009-01-07
The settings are stored in Gconf, (desktop/gnome/file_views/show_backup_files and /desktop/gnome/file_view/show_hidden_files) so you could use gconftool-2 to edit them from command line.

```
gconftool-2 --type boolean --set /desktop/gnome/file_view/show_hidden_files "true"
gconftool-2 --type boolean --set /desktop/gnome/file_view/show_backup_files "true"
```

---

### Post by silverbullet007 on 2009-01-07
Awesome, thanks!

---

### Post by Ptero-4 on 2009-01-07
Also you use the "-a" parameter in the ls tool when you're viewing files from the shell.

---

