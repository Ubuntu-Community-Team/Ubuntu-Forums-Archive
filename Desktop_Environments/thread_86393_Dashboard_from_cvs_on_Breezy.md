---
title: "Dashboard from cvs on Breezy"
date: 2005-11-05
forum: Desktop Environments
---

### Post by munkay on 2005-11-05
I just tried installing dashboard from cvs on to breezy, and the autogen.sh works fine. But when i type "make", it quits with an error:

```
mcs -g -target:library -L ../util/webservices -r:/usr/lib/mono/gtk-sharp/glib-sharp.dll -r:/usr/lib/mono/gtk-sharp/pango-sharp.dll -r:/usr/lib/mono/gtk-sharp/atk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gdk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gtk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gnome-sharp.dll -r:/usr/lib/mono/gtk-sharp/art-sharp.dll -r:/usr/lib/mono/gtk-sharp/gtkhtml-sharp.dll   -r:/usr/lib/mono/gtk-sharp/gconf-sharp.dll -r:/usr/lib/mono/gtk-sharp/gconf-sharp-peditors.dll -r:/usr/lib/mono/gtk-sharp/gnome-sharp.dll -r:/usr/lib/mono/gtk-sharp/glib-sharp.dll -r:/usr/lib/mono/gtk-sharp/pango-sharp.dll -r:/usr/lib/mono/gtk-sharp/atk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gdk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gtk-sharp.dll -r:/usr/lib/mono/gtk-sharp/art-sharp.dll   -r:System.Web -r:../engine/dashboard.exe -r:../util/drive/drive.dll -r:../engine/rdf.dll -out:BeagleBackend.dll ./BeagleBackend.cs ../engine/gnome.cs -r:/usr/lib/beagle/Beagle.dll -r:/usr/lib/beagle/Tiles.dll -r:/usr/lib/beagle/Util.dll
warning CS8029: Compatibility: Use -debug option instead of -g or --debug
warning CS8029: Compatibility: Use -lib:ARG instead of --L arg
../engine/gnome.cs(114,33): warning CS0436: Ignoring imported type `Gnome.VFS.FileInfoOptions' since the current assembly already has a declaration with the same name
../engine/gnome.cs(37,15):: `Gnome.VFS.FileInfoOptions' (name of symbol related to previous warning
/home/bhaskar/Desktop/Downloads/dashboard/engine/dashboard.exe: `Gnome.VFS.FileInfoOptions' (name of symbol related to previous warning
../engine/gnome.cs(99,19): warning CS0436: Ignoring imported type `Gnome.VFS.Result' since the current assembly already has a declaration with the same name
../engine/gnome.cs(44,15):: `Gnome.VFS.Result' (name of symbol related to previous warning
/home/bhaskar/Desktop/Downloads/dashboard/engine/dashboard.exe: `Gnome.VFS.Result' (name of symbol related to previous warning
../engine/gnome.cs(245,10): error CS0433: The imported type `Gnome.ThumbnailFactory' is defined multiple times
/usr/lib/mono/gtk-sharp/gnome-sharp.dll: `Gnome.ThumbnailFactory' (name of symbol related to previous error
/home/bhaskar/Desktop/Downloads/dashboard/engine/dashboard.exe: `Gnome.ThumbnailFactory' (name of symbol related to previous error
../engine/gnome.cs(247,64): warning CS0436: Ignoring imported type `Gnome.VFS.FileInfo' since the current assembly already has a declaration with the same name
../engine/gnome.cs(89,16):: `Gnome.VFS.FileInfo' (name of symbol related to previous warning
/home/bhaskar/Desktop/Downloads/dashboard/engine/dashboard.exe: `Gnome.VFS.FileInfo' (name of symbol related to previous warning
Compilation failed: 1 error(s), 5 warnings
make[1]: *** [BeagleBackend.dll] Error 1
```

Has anyone gotten dashboard working in breezy? and if so, what am I doing wrong?

Thanks for your help.

---

### Post by TomtheWombat on 2006-01-15
Last I checked, even the Dashboard CVS hadn't been updated in a long time.  I believe they changed the Beagle backend and haven't updated Dashboard yet.  (but this was almost a year ago)  Things could have changed, but I doubt it.

---

