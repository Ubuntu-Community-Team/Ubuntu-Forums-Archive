---
title: "Gnome docky causing system to crash."
date: 2009-04-29
forum: Desktop Environments
---

### Post by uni on 2009-04-29
Ok so I can run gnome do's docky and then all of  sudden when i go down to unhide it it will freeze and only thing i can do is move my mouse. I can't logout (ctrl+alt+backspace) nor get into terminal (ctrl+alt+f1). Everything is frozen and i have to hard reset. This has happened 3 times when i try to summon the docky from being hidden. I cant find any help doing google searches. I have no plug ins enabled at the moment or anything. 

here is the output of gnome-do --debug

> [Info  12:15:03.485] [Services] Successfully located service of type IPreferencesService.
[Info  12:15:03.498] [Services] Successfully located service of type ILogService.
[Info  12:15:03.499] [Services] Successfully located service of type ISecurePreferencesService.
[Info  12:15:03.511] [Services] Successfully located service of type INotificationsService.
[Debug 12:15:03.520] [InterfaceManager] "Mini Interface" interface was loaded
[Info  12:15:03.521] [Services] Successfully located service of type ILogService.
[Debug 12:15:03.521] [InterfaceManager] "Docky" interface was loaded
[Debug 12:15:03.522] [InterfaceManager] "Classic Interface" interface was loaded
[Debug 12:15:03.523] [InterfaceManager] "Glass Interface" interface was loaded
[Debug 12:15:03.524] [InterfaceManager] "Nouveau Interface" interface was loaded
[Debug 12:15:03.533] [PluginManager] Loaded "ApplicationItemSource" from plugin.
[Debug 12:15:03.534] [PluginManager] Loaded "GNOMESpecialLocationsItemSource" from plugin.
[Info  12:15:03.537] [Services] Successfully located service of type AbstractApplicationService.
[Debug 12:15:03.540] [PluginManager] Loaded "InternalItemSource" from plugin.
[Debug 12:15:03.540] [PluginManager] Loaded "ItemSourceItemSource" from plugin.
[Debug 12:15:03.541] [PluginManager] Loaded "EmailAction" from plugin.
[Debug 12:15:03.541] [PluginManager] Loaded "OpenAction" from plugin.
[Debug 12:15:03.576] [PluginManager] Loaded "OpenUrlAction" from plugin.
[Debug 12:15:03.576] [PluginManager] Loaded "OpenWithAction" from plugin.
[Debug 12:15:03.576] [PluginManager] Loaded "RevealAction" from plugin.
[Debug 12:15:03.576] [PluginManager] Loaded "RunAction" from plugin.
[Debug 12:15:03.577] [PluginManager] Loaded "CopyToClipboardAction" from plugin.
[Info  12:15:03.583] [Services] Successfully located service of type AbstractSystemService.
[Debug 12:15:03.594] [SystemService] No other application instance detected. Continue startup.
[Info  12:15:03.605] [Services] Successfully located service of type IPreferencesService.
[Info  12:15:03.605] [Services] Successfully located service of type ISecurePreferencesService.
[Debug 12:15:03.615] [Controller] Setting theme Docky
[Info  12:15:03.673] [Services] Successfully located service of type PathsService.
[Info  12:15:03.734] [Services] Successfully located service of type ICoreService.
[Info  12:15:03.938] [UniverseManager] Reloading universe...
[Debug 12:15:03.939] [UniverseManager] Reloading actions...
[Debug 12:15:03.950] [UniverseManager] Reloading item source "Applications"...
[Debug 12:15:04.392] [UniverseManager] Reloading item source "GNOME Special Locations"...
[Debug 12:15:04.409] [UniverseManager] Reloading item source "Internal GNOME Do Items"...
[Debug 12:15:04.411] [UniverseManager] Reloading item source "GNOME Do Item Sources"...
[Info  12:15:04.413] [UniverseManager] Universe contains 265 items.
[Debug 12:15:04.439] [RelevanceProvider] Successfully loaded learned usage data.
[Info  12:15:04.469] [Services] Successfully located service of type IUniverseFactoryService.


everything seems fine to me... 

Im running jaunty with compiz enabled. 

Any help is appreciated, i really like this dock unlike cairo and AWN.

---

### Post by DBO on 2009-05-01
driver issue, what video card do you have?

---

