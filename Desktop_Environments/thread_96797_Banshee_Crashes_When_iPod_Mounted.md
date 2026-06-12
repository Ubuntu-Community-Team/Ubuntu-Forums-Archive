---
title: "Banshee Crashes When iPod Mounted"
date: 2005-11-29
forum: Desktop Environments
---

### Post by bsharitt on 2005-11-29
When ever I try to start Banshee while my iPod is mounted, it won't start, and it crashes if I try to mount the iPod while Banshee is running. The iPod itself mounts fine as far being an external hard drive and gtkpod and Rythmbox can both see it fine as well, so it looks like a problem with Banshee. Here's the terminal output I get while trying to start Banshee with the iPod mounted:

```
Unhandled Exception: IPod.DatabaseReadException: Detected unsupported database version 16
in <0x001b7> IPod.DatabaseRecord:Read (IPod.DatabaseRecord db, System.IO.BinaryReader reader)
in <0x0010e> IPod.SongDatabase:Reload ()
in <0x000b2> IPod.SongDatabase:.ctor (IPod.Device device)
in <0x00033> IPod.Device:get_SongDatabase ()
in [0x00023] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Library.cs:316) Banshee.IpodSource:Refresh ()
in [0x00039] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Library.cs:308) Banshee.IpodSource:.ctor (IPod.Device device)
in [0x000b8] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/SourceView.cs:204) Banshee.SourceView:RefreshList ()
in [0x00139] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/SourceView.cs:162) Banshee.SourceView:.ctor ()
in [0x0025d] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/PlayerInterface.cs:264) Banshee.PlayerUI:BuildWindow ()
in [0x00066] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/PlayerInterface.cs:133) Banshee.PlayerUI:.ctor ()
in [0x0010d] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Main.cs:79) Banshee.BansheeEntry:Main (System.String[] args)
```

Any ideas on how to fix it? The iPod in question is a 2G mini with the latest firmware, FAT32 formatted.

---

### Post by darrenc on 2006-01-20
[QUOTE=bsharitt]When ever I try to start Banshee while my iPod is mounted, it won't start, and it crashes if I try to mount the iPod while Banshee is running. The iPod itself mounts fine as far being an external hard drive and gtkpod and Rythmbox can both see it fine as well, so it looks like a problem with Banshee. Here's the terminal output I get while trying to start Banshee with the iPod mounted:

...

Any ideas on how to fix it? The iPod in question is a 2G mini with the latest firmware, FAT32 formatted.[/QUOTE]

I see the exact same activity when I attach my ipod video, with the following terminal output:

```

Unhandled Exception: IPod.DatabaseReadException: Detected unsupported database version 16
in <0x001b7> IPod.DatabaseRecord:Read (IPod.DatabaseRecord db, System.IO.BinaryReader reader)
in <0x0010e> IPod.SongDatabase:Reload ()
in <0x000b2> IPod.SongDatabase:.ctor (IPod.Device device)
in <0x00033> IPod.Device:get_SongDatabase ()
in [0x00023] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Library.cs:316) Banshee.Ipo dSource:Refresh ()
in [0x00039] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Library.cs:308) Banshee.Ipo dSource:.ctor (IPod.Device device)
in [0x00025] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/SourceView.cs:296) Banshee. SourceView:OnIpodCoreDeviceAdded (System.Object o, Banshee.IpodDeviceArgs args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_IpodDeviceArgs (object,Banshee.Ipod DeviceArgs)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_IpodDeviceArgs (object,Banshee.Ipod DeviceArgs)
in [0x00064] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/IpodCore.cs:88) Banshee.Ipo dCore:OnDeviceAdded (System.Object o, IPod.DeviceAddedArgs args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_DeviceAddedArgs (object,IPod.Device AddedArgs)
in <0x000fc> IPod.DeviceEventListener:DeviceAddedSignalCallback (IntPtr arg0, IntPtr arg1, IntPtr gch)
in (wrapper native-to-managed) IPod.DeviceEventListener:DeviceAddedSignalCallback (intptr,intptr,intptr)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in [0x001b5] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/PlayerInterface.cs:161) Ban shee.PlayerUI:.ctor ()
in [0x0010d] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Main.cs:79) Banshee.Banshee Entry:Main (System.String[] args)
```

Any ideas or suggestions?

Thanks

---

### Post by RagingOcelot on 2006-03-02
I get the same error on loading banshee on a 3G ipod.  Rhythmbox refuses to open too - I think for the same reason.  Amarok works fine, but some things about it just seem quirky to me.  

Have you tried upgrading Banshee to 0.10.6?  I read something on Banshee's site about it playing better with the ipod's database...

---

### Post by RAOF on 2006-03-02
```
Unhandled Exception: IPod.DatabaseReadException: Detected unsupported database version 16
```
This is the reason why it isn't working - you've got a more recent database on the iPod than banshee knows how to access.  This happens quite a lot - new iTunes versions will often silently update your database to the latest version.

As was mentioned, the latest 0.10.6 banshee should work, and will definitely **load**, even if it can't access the iPod.  You should be able to find a more recent banshee in the [http://filefind.net](http://filefind.net) repositories.

---

