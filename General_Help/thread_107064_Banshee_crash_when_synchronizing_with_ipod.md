---
title: "Banshee crash when synchronizing with ipod"
date: 2005-12-22
forum: General Help
---

### Post by Ludwik on 2005-12-22
I use [Banshee]("http://banshee-project.org") 0.10 from [here]("http://packages.filefind.net") on Ubuntu 5.10. Every time I try to update songs to my iPod shuffle Banshee crash:

```
ludwik@leon:~$ banshee

** (/usr/lib/banshee/banshee.exe:8588): WARNING **: Symbol file /usr/lib/mono/gac/dbus-sharp/0.36.2.0__9eef2692033670f5/dbus-sharp.dll.mdb has incorrect version (expected 39, got 38)
Player Engine `Helix Framework Engine (hxclientkit)' failed init tests... disabling (Couldn't create player)
Debug: [2005-12-22 12:37:38] (Changed active player engine) - GStreamer
Debug: [2005-12-22 12:37:38] (Loaded PlayerEngine core) - GStreamer
Debug: [2005-12-22 12:37:38] (Loaded AudioCdPlayerEngine core) - GStreamer
Debug: [2005-12-22 12:37:38] (Audio CD Core Initialized) -
Debug: [2005-12-22 12:37:43] (Registered IO Transaction) - Banshee.SqlLoadTransaction
Debug: [2005-12-22 12:37:43] (Executing IO Transaction) - Banshee.SqlLoadTransaction



Naruszenie ochrony pami&#281;ci

```

Or sometimes:

```
ludwik@leon:~$ banshee

** (/usr/lib/banshee/banshee.exe:8588): WARNING **: Symbol file /usr/lib/mono/gac/dbus-sharp/0.36.2.0__9eef2692033670f5/dbus-sharp.dll.mdb has incorrect version (expected 39, got 38)
Player Engine `Helix Framework Engine (hxclientkit)' failed init tests... disabling (Couldn't create player)
Debug: [2005-12-22 12:37:38] (Changed active player engine) - GStreamer
Debug: [2005-12-22 12:37:38] (Loaded PlayerEngine core) - GStreamer
Debug: [2005-12-22 12:37:38] (Loaded AudioCdPlayerEngine core) - GStreamer
Debug: [2005-12-22 12:37:38] (Audio CD Core Initialized) -
Debug: [2005-12-22 12:37:43] (Registered IO Transaction) - Banshee.SqlLoadTransaction
Debug: [2005-12-22 12:37:43] (Executing IO Transaction) - Banshee.SqlLoadTransaction




(Banshee:8588): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed
Naruszenie ochrony pami&#281;ci

```

I belive "Naruszenie ochrony pami&#281;ci" is Polish version of "segmentation fault".

Thanks for your help...

---

