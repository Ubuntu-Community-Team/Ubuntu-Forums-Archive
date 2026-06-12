---
title: "Banshee Crashed &amp; Now Crashes Everytime I Attempt to Start It"
date: 2011-09-06
forum: Desktop Environments
---

### Post by oxsyn on 2011-09-06
First I restarted - the problem persists.  Then I used apt-get to remove and then install banshee - the problem persists.  Any ideas?

Here's the log:

An unhandled exception was thrown: Object reference not set to an instance of an object

  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo].CheckCacheTable () [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Database.BansheeModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseFilterListModel`2[T,U]..ctor (System.String name, System.String label, Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Hyena.Data.Sqlite.HyenaSqliteConnection connection, Hyena.Data.Sqlite.SqliteModelProvider`1 provider, .U selectAllItem, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseArtistListModel..ctor (Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Banshee.Database.BansheeDbConnection connection, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource+<CreateFiltersFor>c__IteratorB.MoveNext () [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource.DatabaseSourceInitialize () [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order, Banshee.Sources.Source parent) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.PrimarySource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Library.LibrarySource..ctor (System.String label, System.String name, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Library.MusicLibrarySource..ctor () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Run () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.38.11

Assembly Version Information:

gkeyfile-sharp (1.0.0.0)
Banshee.AudioCd (2.0.0.0)
Banshee.CoverArt (2.0.0.0)
Banshee.AmazonMp3 (2.0.0.0)
Banshee.LastfmStreaming (2.0.0.0)
Lastfm (2.0.0.0)
Banshee.Daap (2.0.0.0)
notify-sharp (0.4.0.0)
Banshee.SoundMenu (2.0.0.0)
Banshee.Mpris (2.0.0.0)
Migo (2.0.0.0)
Banshee.Podcasting (2.0.0.0)
Banshee.Dap (2.0.0.0)
Banshee.LibraryWatcher (2.0.0.0)
Banshee.MultimediaKeys (2.0.0.0)
Banshee.Bpm (2.0.0.0)
Banshee.YouTube (2.0.0.0)
Banshee.WebBrowser (2.0.0.0)
Banshee.Wikipedia (2.0.0.0)
Banshee.Lastfm (2.0.0.0)
pango-sharp (2.12.0.0)
Banshee.Fixup (2.0.0.0)
Banshee.Widgets (2.0.0.0)
gio-sharp (2.14.0.0)
gudev-sharp (1.0.0.0)
Banshee.Gio (2.0.0.0)
Banshee.GStreamer (2.0.0.0)
System.Configuration (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (2.0.0.0)
Banshee.NowPlaying (2.0.0.0)
Mono.Cairo (2.0.0.0)
System.Xml (2.0.0.0)
Banshee.Core (2.0.0.0)
Hyena.Data.Sqlite (2.0.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (2.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (2.0.0.0)
Nereid (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
Hyena (2.0.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
System (2.0.0.0)
Banshee.Services (2.0.0.0)
Banshee (2.0.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.38-11-generic x86_64 x86_64 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

[/etc/debian_version]
squeeze/sid

---

### Post by ewz on 2011-09-06
Hiya I had a similar issue with Banshee, I found it was the Notification widget that was causing it to crash, I was able to start Banshee in a Terminal and in the Banshee preferences I was able to disable the widget and all was well :) 
not sure if this will help but its worth a try :)

---

### Post by oxsyn on 2011-09-06
right on - i deleted ~/.config/banshee-1/banshee.db - lost my settings (it was ok since it was a new install), and now it boots fine

---

