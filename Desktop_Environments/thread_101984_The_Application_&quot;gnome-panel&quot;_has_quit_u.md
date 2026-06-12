---
title: "The Application &quot;gnome-panel&quot; has quit unexpectly"
date: 2005-12-11
forum: Desktop Environments
---

### Post by niconi38 on 2005-12-11
Hy everybody,

I've just migrated from hoary to breezy, everythings works well during installation, but I've now a problem : on start-up, I've an error window with this message : "The Application "gnome-panel" has quit unexpectly". I've no menu to launch applications or to launch configuration programs, the task bar is grey and empty, the right-click on it doesn't work...

I've tried several solutions founded on ubuntu forums, principaly french forums :
- reinstalling gnome-panel,
- installing ubuntu-desktop (that was not)
- deleting ./gconf and ./gnome in /home (renaming, not really deleting...)
- deleting .recentlyused.files
- changing theme with gnome-theme-manager

nothing works... :( 
does anybody have another idea ?

Thank you by advance
Nicolas

---

### Post by dcstar on 2005-12-11
[QUOTE=niconi38]Hy everybody,

I've just migrated from hoary to breezy, everythings works well during installation, but I've now a problem : on start-up, I've an error window with this message : "The Application "gnome-panel" has quit unexpectly". I've no menu to launch applications or to launch configuration programs, the task bar is grey and empty, the right-click on it doesn't work...

I've tried several solutions founded on ubuntu forums, principaly french forums :
- reinstalling gnome-panel,
- installing ubuntu-desktop (that was not)
- deleting ./gconf and ./gnome in /home (renaming, not really deleting...)
- deleting .recentlyused.files
- changing theme with gnome-theme-manager

nothing works... :(
does anybody have another idea ?

Thank you by advance
Nicolas[/QUOTE]
I was getting this when I was starting multiple applications in System-Preferences-Session-Startup Programs.

My "fix" was to set the Order of my programs to 51, 52, 53 etc. instead of multiple programs set on 50.

It seems there is a resource issue in the new Gnome in Breezy when too many things try to start simultaneously.

---

