---
title: "Cannot Apply Newest WoW patch"
date: 2007-01-01
forum: Gaming &amp; Leisure
---

### Post by bigspring on 2007-01-01
I recently switched to Ubuntu 6.06 from Windows and am trying to install WoW.  The game installed fine, the patch for 1.12 installed and applied fine and it appeared that the patch for 2.0.1 applied fine as well.  However, when I try to get on the game says that it's version 1.12 still and tries to redownload the patch.  When it goes to update though I get the message "The update could not be applied." Then in box for the reason it states "World of Warcraft has already been installed."

When I try to run the updater from a terminal I get:

fixme:powrprof:DllMain (0x7cf00000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cf00000, 0, (nil)) not fully implemented
fixme:richedit:IRichEditOle_fnGetClientSite stub 0x1343280
fixme:ole:OleCreateStaticFromData (not shown), stub!

when the file opens.

I've tried with both wine 0.9.27 and 0.9.28 in Windows 98, 2000, and XP compatibility modes and when I tried applying the older patch it instead gives the reason for not patching being that I have an up to date version (as it should).

---

### Post by Sammi on 2007-01-02
Maybe the patch file you downloaded was corrupted, and in turn corrupted your WoW installation :(

---

