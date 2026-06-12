---
title: "FSpot fatal error"
date: 2007-02-06
forum: Development CD/DVD Image Testing
---

### Post by lorenco on 2007-02-06
F-Spot crash on startup after fresh install....  (Fresh image of 6 Febtoday)

> An unhandled exception was thrown: GL

  at (wrapper managed-to-native) GdkGlx.Context:glXChooseVisual (intptr,int,int[])
  at GdkGlx.Context..ctor (Gdk.Screen screen, GdkGlx.Context share_list, System.Int32[] attr) [0x00000] 
  at GdkGlx.Context..ctor (Gdk.Screen screen, System.Int32[] attr) [0x00000] 
  at FSpot.PhotoImageView.HandleRealized (System.Object sender, System.EventArgs args) [0x00000] 
  at FSpot.PhotoImageView..ctor (IBrowsableCollection query) [0x00000] 
  at FSpot.PhotoView..ctor (IBrowsableCollection query) [0x00000] 
  at MainWindow..ctor (.Db db) [0x00000] 
  at FSpot.Core.get_MainWindow () [0x00000] 
  at FSpot.Core.Organize () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

google-sharp (0.1.0.0)
FlickrNet (2.1.2.3191)
SmugMugNet (0.0.0.0)
pango-sharp (2.10.0.0)
SemWeb (0.7.1.0)
glade-sharp (2.10.0.0)
gtkhtml-sharp (2.16.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
gdk-sharp (2.10.0.0)
gnome-vfs-sharp (2.16.0.0)
NDesk.DBus (0.0.0.0)
System (2.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (0.0.0.0)
atk-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
f-spot (0.3.2.0)
Mono.GetOptions (2.0.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.20-6-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
4.0

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu feisty (development branch)"

---

### Post by pochu on 2007-02-07
This a know issue.

The workaround is to install libgl1-mesa-dev, and the problem is fixed :D

Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/81578](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/81578)

Best regards
Pochu

---

### Post by lorenco on 2007-02-08
Thanks this works now =D>

---

### Post by kellsens on 2007-02-13
I had this error too, and now it's fixed.
Feisty is great !

---

### Post by pochu on 2007-02-13
kellsens: nice signature :D

---

### Post by kellsens on 2007-02-15
Thank's Pochu !! :-)

---

### Post by drawab on 2007-04-22
I get this error it appears to be different then the one above any clues

```
An unhandled exception was thrown: Object reference not set to an instance of an object

  at FSpot.GalleryAddAlbum.PopulateAlbums () [0x00000] 
  at FSpot.GalleryAddAlbum..ctor (FSpot.GalleryExport export, GalleryRemote.Gallery gallery) [0x00000] 
  at FSpot.GalleryExport.HandleAddAlbum (System.Object sender, System.EventArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000] 
  at (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) Gtk.Application:gtk_main ()
  at Gtk.Application.Run () [0x00000] 
  at Gnome.Program.Run () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 1.1.4322.2032

Assembly Version Information:

System.Web (1.0.5000.0)
System.Xml (1.0.5000.0)
FlickrNet (1.1.0.0)
google-sharp (0.1.0.0)
gconf-sharp (2.16.0.0)
pango-sharp (2.10.0.0)
SemWeb (0.7.1.0)
glade-sharp (2.10.0.0)
gtkhtml-sharp (2.16.0.0)
System.Data (1.0.5000.0)
Mono.Data.SqliteClient (1.0.5000.0)
gdk-sharp (2.10.0.0)
gnome-vfs-sharp (2.16.0.0)
dbus-sharp (0.60.0.0)
System (1.0.5000.0)
Mono.Posix (1.0.5000.0)
atk-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
f-spot (0.2.1.0)
mscorlib (1.0.5000.0)

Platform Information: Linux 2.6.17-11-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"
```

---

### Post by t0n1 on 2008-04-19
Yes, have the same error as the previous poster on Hardy Heron RC.

---

### Post by no2498 on 2010-01-23
fspot is ok on 804
but on 910 karmic it wont do a slide show
just tried it on 910 my other computer

---

