---
title: "Banshee"
date: 2009-04-15
forum: General Help
---

### Post by warrenstroebel@gmail.com on 2009-04-15
I'm having a problem running banshee media player, when i launch it i get the folowing message then it quits:
Banshee encountered a fatal error
error details:
An unhandled exception was thrown: Object reference not set to an instance of an object

  at Banshee.Configuration.DatabaseConfigurationClient.Get (System.String namespce, System.String key) [0x00000] 
  at Banshee.Configuration.DatabaseConfigurationClient.Get[Int32] (System.String namespce, System.String key, Int32 fallback) [0x00000] 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].CheckVersion (System.String namespce, System.String key, Int32 new_version, Banshee.Database.MigrateDel func) [0x00000] 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].CheckVersion () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo].Init () [0x00000] 
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String table_name) [0x00000] 
  at Banshee.Database.BansheeModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Banshee.Database.BansheeDbConnection connection, System.String table_name) [0x00000] 
  at Banshee.Collection.Database.DatabaseTrackModelProvider`1[Banshee.Collection.Database.DatabaseTrackInfo]..ctor (Banshee.Database.BansheeDbConnection connection) [0x00000] 
  at Banshee.Collection.Database.DatabaseTrackInfo.get_Provider () [0x00000] 
  at Banshee.Sources.DatabaseSource.get_TrackProvider () [0x00000] 
  at Banshee.Sources.DatabaseSource.CreateTrackModelFor (Banshee.Sources.DatabaseSource src) [0x00000] 
  at Banshee.Sources.DatabaseSource.get_DatabaseTrackModel () [0x00000] 
  at Banshee.Sources.DatabaseSource+<>c__CompilerGenerated16.MoveNext () [0x00000] 
  at Banshee.Sources.DatabaseSource.DatabaseSourceInitialize () [0x00000] 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order, Banshee.Sources.Source parent) [0x00000] 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] 
  at Banshee.Sources.PrimarySource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] 
  at Banshee.Library.LibrarySource..ctor (System.String label, System.String name, Int32 order) [0x00000] 
  at Banshee.Library.MusicLibrarySource..ctor () [0x00000] 
  at Banshee.ServiceStack.Application.Run () [0x00000] 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] 
  at Nereid.Client..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.27.14

Assembly Version Information:

Banshee.CoverArt (1.4.0.0)
Banshee.MultimediaKeys (1.4.0.0)
Migo (1.4.0.0)
Banshee.Podcasting (1.4.0.0)
Lastfm (1.4.0.0)
Banshee.Lastfm (1.4.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.4.0.0)
Banshee.Bookmarks (1.4.0.0)
Banshee.Daap (1.4.0.0)
Banshee.AudioCd (1.4.0.0)
pango-sharp (2.12.0.0)
Banshee.Widgets (1.4.0.0)
Banshee.Dap.Ipod (1.4.0.0)
Banshee.Dap (1.4.0.0)
Banshee.Hal (1.4.0.0)
Banshee.Unix (1.4.0.0)
Banshee.GStreamer (1.4.0.0)
gconf-sharp (2.20.0.0)
Banshee.Gnome (1.4.0.0)
Banshee.NowPlaying (1.4.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
System.Xml (2.0.0.0)
Mono.Addins (0.3.0.0)
gdk-sharp (2.12.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.4.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (1.4.0.0)
Nereid (1.4.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
Banshee.Core (1.4.0.0)
System (2.0.0.0)
Hyena (1.4.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.4.0.0)
Banshee (1.4.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.27-14-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

[/etc/debian_version]
lenny/sid

any suggestions?

---

### Post by gthou on 2009-04-30
Hi,
I had exactly the same problem.  Removing all banshee related config files solved the issue for me.  Probably some backwards compatibility issue with a new version.

Try:
rm -r ~/.config/banshee-1
rm -r ~/.cache/banshee-1

Guy.

---

### Post by warrenstroebel@gmail.com on 2009-05-17
thanks, worked great.

---

### Post by directhex on 2009-05-18
Gah

Until Banshee's developers get to see a copy of these defective .db files, they'll never be able to fix these bugs

---

