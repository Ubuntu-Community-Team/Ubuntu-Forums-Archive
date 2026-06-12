---
title: "Gnome Mounts."
date: 2007-06-19
forum: Desktop Environments
---

### Post by dholness on 2007-06-19
I have a dual-boot set up, one disc for Win98, one for Ubuntu.  The Windows disc is divided into two FAT32 partitions labelled SYSTEM and USERDATA.  I had Dapper set up to mount these at boot time - they appeard in the Nautilus side panel and I could navigate, read and write file without pa problem.

I've just upgraded (with a great deal of Matrox G400 related pain!) to 7.04, and while I can still access the Windows partitions without a problem, I notice that:

SYSTEM is mounted at /media/winsys.  Both winsys and SYSTEM appear in the Nautilus side pane and drive mount applet.

USERDATA is mounted at /media/windows.  Both windows and USERDATA appear in the Nautilus side pane and drive mount applet.

I cannot mount SYSTEM or USERDATA through Nautilus or the applet (they are after all already mounted) or remove them from the side panel.  This is irritating by the way, not serious.

Does anyone know how I can avoid seeing the same storage locations twice?  Why doesn't Gnome realise that these partitions are already mounted?  I suspect that the GCONF will fix this, but I don't know how.

Thanks for your time.

---

