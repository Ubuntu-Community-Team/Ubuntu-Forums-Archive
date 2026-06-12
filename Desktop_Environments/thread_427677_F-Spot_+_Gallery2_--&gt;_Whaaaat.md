---
title: "F-Spot + Gallery2 --&gt; Whaaaat?"
date: 2007-04-29
forum: Desktop Environments
---

### Post by miobio on 2007-04-29
Ok,

I upgraded to fiesty in these last days and I noticed something really funny :-S (rather sad than funny ... )

I run a gallery2 site on my little server at home and I use it to share pictures with my friends exporting them from F-Spot.

Now, the new version of F-Spot requires ver. >=1.0.8 of gallery2's "Remote" module, I am running the latest version of gallery2 (2.2.1-2) straight from ubuntu's universe repo (I think...), this comes with ver. 1.0.6 of the "Remote" module :-S

I tried to install the 1.0.8 and/or 1.0.6 modules but it complains about a wrong version of gallery core. 

I know there's a patch for F-Spot that ***seems*** to cope with this ~~~little~~~ issue but I don't have the time nor the knowledge to recompile F-Spot from scratch.


Anyone on this? :-(

---

### Post by miobio on 2007-04-30
UPDATE:

I have upgraded my version of gallery2 to the latest nightly build (2.3).

This comes with remote 1.0.11

Surprisingly ... I still get the same err from F-Spot:

```

An unhandled exception was thrown: Error: Unable to parse server response

  at GalleryRemote.Gallery.ParseBasic (System.Net.HttpWebResponse response) [0x00000] 
  at GalleryRemote.Gallery.ParseNewAlbum (System.Net.HttpWebResponse response) [0x00000] 
  at GalleryRemote.Gallery2.NewAlbum (System.String parent_name, System.String name, System.String title, System.String description) [0x00000] 
  at FSpot.GalleryAddAlbum.HandleAddResponse (System.Object sender, Gtk.ResponseArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_ResponseArgs (object,Gtk.ResponseArgs)
  at Gtk.Dialog.ResponseSignalCallback (IntPtr arg0, Int32 arg1, IntPtr gch) [0x00000] 
  at (wrapper native-to-managed) Gtk.Dialog:ResponseSignalCallback (intptr,int,intptr)
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) Gtk.Application:gtk_main ()
  at Gtk.Application.Run () [0x00000] 
  at Gnome.Program.Run () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

System.Web (2.0.0.0)
Mono.Security (2.0.0.0)
System.Configuration (2.0.0.0)
System.Xml (2.0.0.0)
google-sharp (0.1.0.0)
FlickrNet (2.1.2.19557)
SmugMugNet (0.0.0.0)
pango-sharp (2.10.0.0)
SemWeb (0.7.1.0)
glade-sharp (2.10.0.0)
gtkhtml-sharp (2.16.0.0)
System.Transactions (2.0.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
gdk-sharp (2.10.0.0)
gnome-vfs-sharp (2.16.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System (2.0.0.0)
Mono.Posix (2.0.0.0)
atk-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
f-spot (0.3.5.0)
Mono.GetOptions (2.0.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.20-15-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
4.0

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"

```

I'm going to fill a bug in launchpad.

---

### Post by miobio on 2007-04-30
New bug on launchpad posted.

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/111272](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/111272)

I found loads of Gallery2 related bugs but none seems to be the one I'm experiencing...

---

