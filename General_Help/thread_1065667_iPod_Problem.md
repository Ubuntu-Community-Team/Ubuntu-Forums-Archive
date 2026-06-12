---
title: "iPod Problem"
date: 2009-02-10
forum: General Help
---

### Post by thestig_992 on 2009-02-10
Hey everyone,

I just bought a new iPod nano (2G), and i have a few issues transfering music to it. I used to have a mini, and used amarok with that. With the nano though, amarok really screws up (im using amarok 2 now instead of 1, so im still learning where everything is). So i decided to use Hippo to transfer stuff, but i get this error everytime, and i have no idea what it means:

```
at IPod.DatabaseRecord.Read (IPod.DatabaseRecord db, System.IO.BinaryReader reader) [0x00000] 
  at IPod.TrackDatabase.Reload (Boolean createFresh) [0x00000] 
  at IPod.TrackDatabase..ctor (IPod.Device device, Boolean createFresh) [0x00000] 
  at IPod.Device.LoadTrackDatabase (Boolean createFresh) [0x00000] 
  at IPod.Device.LoadTrackDatabase () [0x00000] 
  at IPod.Device.get_TrackDatabase () [0x00000] 
  at IPod.Device.get_Name () [0x00000] 
  at IPod.DeviceCombo.AddDevice (IPod.Device device) [0x00000] 
  at IPod.DeviceCombo..ctor () [0x00000] 
  at Hipo.HipoMainWindow.CreateWindow (System.String[] args) [0x00000] 
  at Hipo.HipoMain.Run (System.String[] args) [0x00000] 
  at Hipo.HipoMain.Main (System.String[] args) [0x00000] 
```

Hipo works perectly with my old ipod, but not the new one...any suggestions?

---

