---
title: "Gnome shell crashes when Virtualbox started"
date: 2011-12-02
forum: Desktop Environments
---

### Post by Jim_in_Omaha on 2011-12-02
FYI:

If you run into trying to start VirtualBox and it crashes Gnomeshell 3.2, try reinstalling your video drivers.

Mine started doing this within the last couple of days. Not sure what update or change I made could have done this. But it posted

Watcher  ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={c28be65f-1a8f-43b4-81f1-eb60cb516e66} aComponent={VirtualBox} aText={The object is not ready}, preserve=false

in the VBoxSVC.log file.

I use Nvidia, so I just removed it propriety drivers, rebooted, reinstalled, rebooted again and it is fixed.

---

