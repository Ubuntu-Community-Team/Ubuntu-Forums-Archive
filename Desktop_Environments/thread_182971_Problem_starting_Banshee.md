---
title: "Problem starting Banshee"
date: 2006-05-27
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-05-27
Banhee won't start for me.  Here's what I'm getting:

```

myusername@cpc1-eswd2-4-1-cust78:~$ banshee

** (/usr/lib/banshee/banshee.exe:18592): WARNING **: Symbol file /usr/lib/banshee/banshee.exe.mdb has incorrect version (expected 38, got 39)

** (/usr/lib/banshee/banshee.exe:18592): WARNING **: Symbol file /usr/lib/banshee/Banshee.Base.dll.mdb has incorrect version (expected 38, got 39)

** (/usr/lib/banshee/banshee.exe:18592): WARNING **: Symbol file /usr/lib/banshee/Banshee.Widgets.dll.mdb has incorrect version (expected 38, got 39)
Warning: [27/05/2006 09:46:23] (Cannot connect to NetworkManager) - An available, working network connection will be assumed

** (<unknown>:18592): WARNING **: Symbol file /usr/lib/banshee/Banshee.MediaEngine/Gstreamer/gst-player.dll.mdb has incorrect version (expected 38, got 39)
Debug: [27/05/2006 09:46:26] (Changed active playback engine) - GStreamer
Debug: [27/05/2006 09:46:26] (Loaded primary playback engine) - GStreamer
Debug: [27/05/2006 09:46:26] (Loaded Audio CD playback engine) - GStreamer

** (<unknown>:18592): WARNING **: Symbol file /usr/lib/banshee/hal-sharp.dll.mdb has incorrect version (expected 38, got 39)
Debug: [27/05/2006 09:46:27] (Audio CD Core Initialized) -

** (<unknown>:18592): WARNING **: Symbol file /usr/lib/banshee/Banshee.Dap/Banshee.Dap.Ipod.dll.mdb has incorrect version (expected 38, got 39)

** (<unknown>:18592): WARNING **: Symbol file /usr/lib/banshee/Banshee.Dap/Banshee.Dap.Njb.dll.mdb has incorrect version (expected 38, got 39)
Warning: [27/05/2006 09:46:28] (Could not process connected DAP) - Failed to create device

Unhandled Exception: System.DllNotFoundException: libdbus-1.so.2
in (wrapper managed-to-native) Hal.DBusError:dbus_error_init (intptr)
in <0x0006f> Hal.DBusError:.ctor ()
in <0x00025> Hal.Device:set_WatchProperties (Boolean value)
in <0x001b3> Banshee.Dap.DapCore:AddDevice (Hal.Device device, System.Type type)in <0x0006a> Banshee.Dap.DapCore:AddDevice (Hal.Device device)
in <0x00050> Banshee.Dap.DapCore:BuildDeviceTable ()
in <0x00033> Banshee.Dap.DapCore:Initialize ()
in <0x00139> Banshee.Base.Globals:Initialize ()
in <0x0046f> Banshee.BansheeEntry:Startup (System.String[] args)
in <0x0000a> Banshee.BansheeEntry:Main (System.String[] args)

```

There may be a conflict with Nautilus.  The above is what I get when I have a file manager open.  If I don't - it *will* start - but whan I plug in my iPod and it automounts and a manager opens - Banhee bombs out.

Any ideas?  I'm desparate to try Banshee for iPod management because gtkpod keeps giving errors when I sync.

---

### Post by xyz on 2006-05-27
Have you tried visiting their homepage?
[http://banshee-project.org/Distributions/Ubuntu](http://banshee-project.org/Distributions/Ubuntu)

---

### Post by Edward The Bonobo on 2006-05-28
Yeah...they suggest that the Breezy reps version might not be the latest.  I added their rep to my sources.list and reinstalled...but synaptic said I already had the latest version.  Reinstalled anyway...but it still doesn't work.

---

