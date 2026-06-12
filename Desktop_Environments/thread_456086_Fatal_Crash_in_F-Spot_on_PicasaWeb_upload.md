---
title: "Fatal Crash in F-Spot on PicasaWeb upload"
date: 2007-05-27
forum: Desktop Environments
---

### Post by pilchinsky on 2007-05-27
Hi,
I get the following Fatail Error when I try to upload photos using F-Spot onto PicasaWeb

I tried looking everywhere for a way to reconfigure F-Spot,  does anyone know where this can be done? I really want to change the login information it's using for PicasaWeb. 

An unhandled exception was thrown: Object reference not set to an instance of an object

  at Mono.Google.Picasa.PicasaWeb.GetAlbums () [0x00000] 
  at FSpot.GoogleExport.PopulateAlbumOptionMenu (Mono.Google.Picasa.PicasaWeb picasa) [0x00000] 
  at FSpot.GoogleExport.Connect (FSpot.GoogleAccount selected, System.String token, System.String text) [0x00000] 
  at FSpot.GoogleExport.Connect (FSpot.GoogleAccount selected) [0x00000] 
  at FSpot.GoogleExport.Connect () [0x00000] 
  at FSpot.GoogleExport..ctor (IBrowsableCollection selection) [0x00000] 
  at MainWindow.HandleExportToPicasa (System.Object sender, System.EventArgs args) [0x00000] 
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

Mono.Security (1.0.5000.0)
System.Web (1.0.5000.0)
System.Xml (1.0.5000.0)
gnome-keyring-sharp (0.0.0.0)
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

---

