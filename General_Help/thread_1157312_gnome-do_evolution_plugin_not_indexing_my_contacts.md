---
title: "gnome-do evolution plugin not indexing my contacts"
date: 2009-05-12
forum: General Help
---

### Post by lompa on 2009-05-12
Hi

I recently installed gnome-do on jaunty (on a 64 bit machine); I'm having problems with the evolution plugin, which appears not to be indexing my contacts. I'm getting no exception at all when running "[FONT="Courier New"]gnome-do --debug[/FONT]", unlike in posts [https://answers.launchpad.net/do/+question/49322]("https://answers.launchpad.net/do/+question/49322") or [https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/348630]("https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/348630"). I've libevolution5.0-cil installed. Any hint? Anyone with the same problem? The workaround for interpid posted at [https://bugs.launchpad.net/do/+bug/292622/comments/2]("https://bugs.launchpad.net/do/+bug/292622/comments/2") did not work.

Here's an extract of the output of "[FONT="Courier New"]gnome-do --debug[/FONT]":
```
[Debug 21:38:47.778] [PluginManager] Loaded "GNOMESpecialLocationsItemSource" from plugin.
[Info  21:38:47.781] [Services] Successfully located service of type AbstractApplicationService.
[Debug 21:38:47.784] [PluginManager] Loaded "InternalItemSource" from plugin.
[Debug 21:38:47.784] [PluginManager] Loaded "ItemSourceItemSource" from plugin.
[Info  21:38:47.788] [Services] Successfully located service of type PathsService.
[Debug 21:38:47.812] [PluginManager] Loaded "AliasItemSource" from plugin.
[Debug 21:38:47.813] [PluginManager] Loaded "ContactItemSource" from plugin.
[Debug 21:38:47.814] [PluginManager] Loaded "BookmarkItemSource" from plugin.
[Debug 21:38:47.814] [PluginManager] Loaded "NotesItemSource" from plugin.

```

The evolution plugin seems to be related to item "ContactItemSource".

Thank a lot in advance!

Lompa

---

