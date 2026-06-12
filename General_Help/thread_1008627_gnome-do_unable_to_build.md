---
title: "gnome-do: unable to build"
date: 2008-12-11
forum: General Help
---

### Post by giacomo on 2008-12-11
I'm able to add gnome-do to my ubuntu system using apt-get/synaptic, but I'd like to build the source 'bzr'-ed from launch-pad.

The command
```
./autogen.sh
```
completes without problems, but
```
make
```
fails with
```

./src/Do.UI/MonoDock/MonoDock.UI/DockArea.cs(274,27): error CS0507: `MonoDock.UI.DockArea.State.get': cannot change access modifiers when overriding `internal' inherited member `Gtk.Widget.State.get'
/usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous error)
./src/Do.UI/MonoDock/MonoDock.UI/DockArea.cs(274,27): warning CS0108: `MonoDock.UI.DockArea.State' hides inherited member `Gtk.Widget.State'. Use the new keyword if hiding was intended
/usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous warning)
./src/Do.UI/MonoDock/MonoDock.UI/DockWindow.cs(163,59): warning CS0108: `MonoDock.UI.DockWindow.KeyPressEvent' hides inherited member `Gtk.Widget.KeyPressEvent'. Use the new keyword if hiding was intended
/usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous warning)
./src/Do.UI/MonoDock/MonoDock.UI/DockWindow.cs(214,29): warning CS0108: `MonoDock.UI.DockWindow.Visible' hides inherited member `Gtk.Widget.Visible'. Use the new keyword if hiding was intended
/usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous warning)
Compilation failed: 1 error(s), 3 warnings
make[1]: *** [bin/Debug/Do.Addins.dll] Error 1
make[1]: Leaving directory `/home/developer/src/do/Do.Addins'
make: *** [all-recursive] Error 1

```

Any idea? All deps, I think, were installed properly...
Thanks in advance!

---

### Post by directhex on 2008-12-11
File a bug with Do upstream. Looks like either a code error, or a compatibility problem with GTK# 2.12

---

### Post by giacomo on 2008-12-12
Thanks for reply.
I filed the bug before posting in this forum.

Bye

---

