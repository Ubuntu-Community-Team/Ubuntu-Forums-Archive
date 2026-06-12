---
title: "monodevelop from svn error on make"
date: 2006-08-28
forum: Desktop Environments
---

### Post by binks on 2006-08-28
i get this error when i run make 

[http://paste.ubuntu-nl.org/21898](http://paste.ubuntu-nl.org/21898)

./MonoDevelop.Ide.Gui.Dialogs/FileSelectorDialog.cs(122,5): warning CS0612: `Gtk.OptionMenu' is obsolete
./MonoDevelop.Ide.Gui/HelpViewer.cs(36,4): error CS1502: The best overloaded method match for `Gtk.Container.Add(Gtk.Widget)' has some invalid arguments
./MonoDevelop.Ide.Gui/HelpViewer.cs(36,4): error CS1503: Argument 1: Cannot convert from `Gtk.HTML' to `Gtk.Widget'
Compilation failed: 2 error(s), 17 warnings
make[3]: *** [../../../build/AddIns/MonoDevelop.Ide.dll] Error 1
make[3]: Leaving directory `/home/binks/monodevelop/Core/src/MonoDevelop.Ide'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/binks/monodevelop/Core/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/binks/monodevelop/Core'
make: *** [all-recursive] Error 1


any help please

---

