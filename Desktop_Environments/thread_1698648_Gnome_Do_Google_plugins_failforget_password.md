---
title: "Gnome Do: Google plugins fail/forget password"
date: 2011-03-02
forum: Desktop Environments
---

### Post by gradysghost on 2011-03-02
Here's the problem in a nutshell.  There are four plugins for Gnome Do related to Google services.  I use three of them.  I use Google Contacts, Google Calendar, and Google Docs.  I go into the configuration details for each, set and verify the password, and get out.  When I invoke Do and start typing (for example, if I start typing "Grocery List", one of the results should be the grocery list Google Doc that my wife and I share), they all work.

Inevitably, I'll log off, and when I come back, none of these plugins work.  They act as though they don't remember my password.  I have to enter my password each time.  This is the case if I log off or even just stop the gnome-do process and start it again.  It always always always "forgets" my password, and I have to re-enter it for all three of these plugins.

Perhaps you'd like to see Do's output on launch.

```
$ gnome-do --debug

(Do:4639): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(Do:4639): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(Do:4639): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(Do:4639): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",
WARNING: [Do.Banshee,1.0] Could not load some add-in assemblies: File '/usr/lib/banshee-1/Banshee.CollectionIndexer.dll' not found.
ERROR: Errors found in add-in '/usr/lib/gnome-do/Banshee.dll:
ERROR: The file '/usr/lib/banshee-1/Banshee.CollectionIndexer.dll' referenced in the manifest could not be found.
[Info  14:12:56.862] [Services] Successfully located service of type IPreferencesService.
[Info  14:12:56.868] [Services] Successfully located service of type ILogService.
[Info  14:12:56.868] [Services] Successfully located service of type ISecurePreferencesService.
[Info  14:12:56.871] [Services] Successfully located service of type INotificationsService.
[Debug 14:12:56.873] [InterfaceManager] "Docky" interface was loaded
[Info  14:12:56.874] [Services] Successfully located service of type ILogService.
[Debug 14:12:56.874] [InterfaceManager] "Mini" interface was loaded
[Debug 14:12:56.874] [InterfaceManager] "Classic" interface was loaded
[Debug 14:12:56.875] [InterfaceManager] "Glass" interface was loaded
[Debug 14:12:56.875] [InterfaceManager] "Nouveau" interface was loaded
[Info  14:12:56.880] [Services] Successfully located service of type IPreferencesService.
[Info  14:12:56.880] [Services] Successfully located service of type ISecurePreferencesService.
[Info  14:12:56.882] [Services] Successfully located service of type ICoreService.
[Info  14:12:56.884] [Services] Successfully located service of type INetworkService.
[Debug 14:12:56.886] [PluginManager] Loaded "WeatherItemSource" from plugin.
[Info  14:12:56.887] [Services] Successfully located service of type AbstractApplicationService.
[Debug 14:12:56.888] [PluginManager] Loaded "InternalItemSource" from plugin.
[Debug 14:12:56.888] [PluginManager] Loaded "ItemSourceItemSource" from plugin.
[Debug 14:12:56.891] [PluginManager] Loaded "GDocsItemSource" from plugin.
[Debug 14:12:56.892] [PluginManager] Loaded "ApplicationItemSource" from plugin.
[Debug 14:12:56.892] [PluginManager] Loaded "GNOMESpecialLocationsItemSource" from plugin.
[Debug 14:12:56.892] [PluginManager] Loaded "GCalendarItemSource" from plugin.
[Debug 14:12:56.893] [PluginManager] Loaded "ProfileItemSource" from plugin.
[Debug 14:12:56.893] [PluginManager] Loaded "SessionCommandsItemSource" from plugin.
[Debug 14:12:56.893] [PluginManager] Loaded "FileItemSource" from plugin.
[Debug 14:12:56.895] [PluginManager] Loaded "RecentFileItemSource" from plugin.
[Debug 14:12:56.896] [PluginManager] Loaded "GMailItemSource" from plugin.
[Debug 14:12:56.897] [PluginManager] Loaded "EmailAction" from plugin.
[Debug 14:12:56.897] [PluginManager] Loaded "OpenAction" from plugin.
[Debug 14:12:56.911] [PluginManager] Loaded "OpenUrlAction" from plugin.
[Debug 14:12:56.911] [PluginManager] Loaded "OpenWithAction" from plugin.
[Debug 14:12:56.911] [PluginManager] Loaded "RevealAction" from plugin.
[Debug 14:12:56.911] [PluginManager] Loaded "RunAction" from plugin.
[Debug 14:12:56.912] [PluginManager] Loaded "DefineAction" from plugin.
[Debug 14:12:56.912] [PluginManager] Loaded "GDocsUploadDocument" from plugin.
[Debug 14:12:56.912] [PluginManager] Loaded "GDocsTrashDocument" from plugin.
[Debug 14:12:56.912] [PluginManager] Loaded "CopyToClipboardAction" from plugin.
[Debug 14:12:56.912] [PluginManager] Loaded "GCalendarNewEvent" from plugin.
[Debug 14:12:56.912] [PluginManager] Loaded "GCalendarSearchEvents" from plugin.
[Debug 14:12:56.912] [PluginManager] Loaded "ViewCalendarAction" from plugin.
[Debug 14:12:56.912] [PluginManager] Loaded "ViewEventAction" from plugin.
[Debug 14:12:56.912] [PluginManager] Loaded "RunInTerminalAction" from plugin.
[Debug 14:12:56.913] [PluginManager] Loaded "OpenTerminalHereAction" from plugin.
[Debug 14:12:56.913] [PluginManager] Loaded "NewFileAction" from plugin.
[Debug 14:12:56.913] [PluginManager] Loaded "NewFolderAction" from plugin.
[Debug 14:12:56.913] [PluginManager] Loaded "CopyAction" from plugin.
[Debug 14:12:56.913] [PluginManager] Loaded "MoveAction" from plugin.
[Debug 14:12:56.913] [PluginManager] Loaded "RenameAction" from plugin.
[Debug 14:12:56.913] [PluginManager] Loaded "MoveToTrashAction" from plugin.
[Debug 14:12:56.913] [PluginManager] Loaded "RecentConversationsActions" from plugin.
[Debug 14:12:56.914] [PluginManager] Loaded "InlineGoogleSearch" from plugin.
[Debug 14:12:56.914] [PluginManager] Loaded "ImFeelingLucky" from plugin.
[Info  14:12:56.914] [Services] Successfully located service of type AbstractSystemService.
[Debug 14:12:56.915] [SystemService] No other application instance detected. Continue startup.
[Debug 14:12:56.930] [Controller] Setting theme Glass
[Info  14:12:56.974] [UniverseManager] Reloading universe...
[Debug 14:12:56.974] [UniverseManager] Reloading actions...
[Debug 14:12:56.981] [UniverseManager] Reloading item source "Weather Commands"...
[Debug 14:12:56.982] [UniverseManager] Reloading item source "Internal GNOME Do Items"...
[Debug 14:12:56.982] [UniverseManager] Reloading item source "GNOME Do Item Sources"...
[Debug 14:12:57.057] [UniverseManager] Reloading item source "Google Docs"...
[Debug 14:12:57.058] [UniverseManager] Reloading item source "Applications"...
[Debug 14:12:57.136] [UniverseManager] Reloading item source "GNOME Special Locations"...
[Debug 14:12:57.146] [UniverseManager] Reloading item source "Google Calendars"...
[Debug 14:12:57.147] [UniverseManager] Reloading item source "GNOME Terminal Profiles"...
[Debug 14:12:57.154] [UniverseManager] Reloading item source "GNOME Session Commands"...
[Debug 14:12:57.154] [UniverseManager] Reloading item source "Files and Folders"...
[Info  14:12:57.158] [Services] Successfully located service of type PathsService.
[Debug 14:12:57.179] [IndexedFolderCollection] Loaded Files and Folders plugin state.
[Info  14:12:57.189] [Services] Successfully located service of type IUniverseFactoryService.
[Debug 14:12:57.197] [UniverseManager] Reloading item source "Recent Files"...
[Debug 14:12:57.199] [UniverseManager] Reloading item source "GMail Contacts"...
[Info  14:12:57.200] [UniverseManager] Universe contains 260 items.
[Info  14:12:57.202] [AbstractWeatherSource] Weather Underground: Reloading weather data
[Debug 14:12:57.204] [AbstractWeatherSource] Weather Underground: Fetching XML file 'http://api.wunderground.com/auto/wui/geo/WXCurrentObXML/index.xml?query=50014'
[Debug 14:12:59.505] Retrieved 415 contacts
[Debug 14:13:02.480] [AbstractWeatherSource] Weather Underground: Fetching XML file 'http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=50014'
[Debug 14:13:13.699] [RelevanceProvider] Successfully loaded learned usage data.
```

So no errors.  In fact, it says it's successfully loaded my contacts, but it's not giving them to me when I search.  Nor is it giving me my docs or calendar events.  This is the crux of the problem.

So I started doing some research on the problem.  I also happen to use Docky (the standalone product, not the method of running Gnome Do), and I use the Gmail docklet with it.  This one has no problems "remembering" my password.  So I started looking into how it works.  It stores my password in my default keyring.  So I started to dig around in there.

The docklet stores its password in a keyring password called

```
docky-2/GMail/GMailPreferences/Password
```

There also exist several other keys that appear to be related to the Do plugins:

```
gnome-do/GMail/GMailPreferences/Password
gnome-do/GDocs/GDocsPreferences/Password
gnome-do/GCalendar/GCalPreferences/Password
```

If I go into the details of each of these, my correct password is clearly visible in the Password field.  So I have to conclude that the problem has something to do with the way Do loads this password.  However, there is no output suggesting what the problem actually is.

Does anybody have any ideas?

Oh, version numbers: Do (0.8.3.1); Do Plugins (0.8.2.1); Docky (2.0.12).  These version numbers are what I get from a dpkg-query, for whatever that's worth.

Please help!

---

