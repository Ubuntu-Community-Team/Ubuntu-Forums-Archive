---
title: "Several Applications Failing, Help Needed"
date: 2011-05-08
forum: Desktop Environments
---

### Post by Erebus1 on 2011-05-08
Ever since I loaded 11.04 onto my computer a few days ago, no media applications, i.e. Rhythmbox and Banshee, have both failed, and Evolution has been experiencing some glitches as well.  

Whenever I launch Rhythmbox, the window shows up as normal, but then a second later, the application crashes.  I have no idea why this is, only that it is a huge pain in the neck.  Whenever I launch Banshee, a popup comes up that says > Encountered a fatal error.
Exception has been thrown by the target of an invocation.  The drop-down icon labeled "Error Details" reads:
```
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
OS Version: Unix 2.6.38.8

Assembly Version Information:

Banshee.AudioCd (2.0.0.0)
Banshee.CoverArt (2.0.0.0)
Banshee.AmazonMp3 (2.0.0.0)
Banshee.Daap (2.0.0.0)
notify-sharp (0.4.0.0)
Banshee.SoundMenu (2.0.0.0)
Banshee.Mpris (2.0.0.0)
Lastfm (2.0.0.0)
Banshee.Dap (2.0.0.0)
Migo (2.0.0.0)
Banshee.Podcasting (2.0.0.0)
Banshee.MultimediaKeys (2.0.0.0)
Banshee.Bpm (2.0.0.0)
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

Platform Information: Linux 2.6.38-8-generic-pae i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

[/etc/debian_version]
squeeze/sid


```

Also, before I updated, I used the Evolution RSS plugin to subscribe to webcomics and blogs and such, but when I installed it again into 11.04 (I wiped the drive, that's why I say "again"), the application window shows up, but then after that, it is unresponsive, even the close button, sometimes.  

Does anyone have any idea as to why these applications are malfunctioning as they are, and if so, can you help? 
Thanks in advance.

[Edit]
Also, for some reason, a popup window that says > Items cannot be installed or removed until the package catalog is repaired.  Do you want to repair it now? pops up when I open the Software Center to remove the plugin.  When I click "OK," it asks for my password once, then the popup appears again.  When I try to launch the Update Manager to perform the tasks without the middleman of the Software Center, it crashes after it finishes building data structures.  Any idea how to fix this?

---

### Post by cvielma on 2011-05-09
Hi! It's too bad what happened :s Time ago this was common in Ubuntu when doing distro-upgrade, but since a couple of years my experience is that it work flawlessly.

But well, my recommendation is to do a complete reinstall using a live cd... But if you want to try recover your actual installation, try to do a downgrade first (i had never done that). Here is a guide for you to do that: [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

And then try a new upgrade but close the application while the system is upgrading. Maybe something is lost when doing the upgrade, or something failed and passed unnoticed.

Hope that helps.

Best regards,

---

### Post by Erebus1 on 2011-05-10
Thanks for your response, but it seems I was unclear in my original post.  When I upgraded, I decided to completely wipe the drive; I didn't upgrade from 10.10, I started over, so there shouldn't have been any files left over from Maverick.

Also, the problem with the Software Center was resolved.

---

### Post by cvielma on 2011-05-10
Ah ok!

Can you check if the cd/usb that you used to upgrade is fine? (i mean, if you can checksum it)

All the applications worked well before the upgrade? When you installed 11.04 did you erase / partition? maybe it only reinstalled over it...

Hope it helps.

Best regards,

---

### Post by mörgæs on 2011-05-11
There are a lot of similar reports of media players not working. I would stay with 10.10 at least for a couple of months more (or maybe as long as it is supported).

---

### Post by Erebus1 on 2011-06-03
When I reinstalled, I formatted the drive, so I couldn't have installed over it.  

Also, I just reinstalled from a CD (the first time, I used a flash drive) and reformatted (that can't be too good for the computer, can it?), and now I'm having troubles with the update manager; it won't install new software, and whenever I try, it says > "An handleable error occurred," and that > "There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks."  I'm not sure what's wrong, because it will install one or two packages at a time, but only certain types, none of which are apt, which might solve the problem (I think).

---

### Post by mörgæs on 2011-06-05
Reformatting is not damaging. Actually it is the best you can do, if you can not proceed in other ways to get a problem solved.

For the update problems, try to boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Please post the error messages, if any.

---

### Post by Erebus1 on 2011-06-06
You, sir, are a life saver.  Thank you very much.

---

### Post by Erebus1 on 2011-06-06
So the problem with the updates was fixed, but I'm still having trouble with several applications.  The biggest problem is Chromium, which will randomly kill pages, or even shut down altogether.  Evolution won't allow me to add RSS feeds, and will freeze up every time I try to do so (I installed the evolution-rss extension).

Do you have any idea of how to deal with that?

---

### Post by wildmanne39 on 2011-06-07
> **Erebus1 said:**
> So the problem with the updates was fixed, but I'm still having trouble with several applications.  The biggest problem is Chromium, which will randomly kill pages, or even shut down altogether.  Evolution won't allow me to add RSS feeds, and will freeze up every time I try to do so (I installed the evolution-rss extension).

Do you have any idea of how to deal with that?
Hi, a lot of people are having trouble with Chromium, so they have switched to chrome, you can download and install if from google for linux. I am not sure about your other problem.

---

