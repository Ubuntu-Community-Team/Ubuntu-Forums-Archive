---
title: "Kde &amp; Kmenu giant icons problem"
date: 2005-10-24
forum: Desktop Environments
---

### Post by Luther on 2005-10-24
Hi there, 
I've upgraded Ubuntu to Breezy last night and besides some minor issue somthing strange happens inside kde:
when some icons (svg) are displayed by kmenu they seem oversized, too big to be displayed !
I see this is related to the icon theme currently installed (IcOsX theme).
example are a giant "Find" icon, "More Application" icon, "scanner" etc..
This completly screw up the layout of the menus.
Not strangely enough, others icons for others menu entries from the very same icons set seem to be sized correctly.
Why is that??
In the previous kde version everything was working as should be.
Is it an upgrade issue or a kde version issue?
How could I workaround from this problem?
I don't see any settings to force icons size for menu entries :(

Saluther

---

### Post by mlomker on 2005-10-24
On the Run Command line type in **kdesu kcontrol**.  Go into Appearance & Themes, Icons, Advanced.  You'll see some adjustments for icon font sizes.

---

### Post by Luther on 2005-10-27
Already tried but the panel icon entry is disable and I cannot change or force the size. Could someone try this icon theme?
[http://pldun.free.fr/icosx-0.7.tar.gz](http://pldun.free.fr/icosx-0.7.tar.gz)
and tell me if it's a common issue? 
Perhaps it's changed something in the icon theme management and the theme have to be upgraded.

bye

---

### Post by shakin on 2005-10-28
[QUOTE=Luther]Already tried but the panel icon entry is disable and I cannot change or force the size. Could someone try this icon theme?
[http://pldun.free.fr/icosx-0.7.tar.gz](http://pldun.free.fr/icosx-0.7.tar.gz)
and tell me if it's a common issue? 
Perhaps it's changed something in the icon theme management and the theme have to be upgraded.

bye[/QUOTE]

I think I've tried that theme before, or one like it, and I remember it had huge icons.

---

### Post by Luther on 2005-10-28
I've found it!
Seems that kde doesn't like the "index.desktop" file distribuited with that theme but you can't only add a copy of "index.theme" as suggested [here]("http://www.kde-look.org/content/show.php?content=2242")
you must delete (or move) original index.desktop so index.theme will be sourced by kicker at startup.
The "index.theme" is this one:
---
> [Icon Theme]
Name=IcOSX
DisplayDepth=32

Inherits=hicolor

Example=folder
LinkOverlay=link
LockOverlay=lockoverlay
ShareOverlay=share
ZipOverlay=zip
DesktopDefault=48
DesktopSizes=16,22,32,48,64,128
ToolbarDefault=22
ToolbarSizes=16,22,32,48
MainToolbarDefault=22
MainToolbarSizes=16,22,32,48
SmallDefault=16
SmallSizes=16
PanelDefault=32
PanelSizes=16,22,32,48,64,128
Directories=16x16/actions,16x16/apps,16x16/devices,16x16/filesystems,16x16/mimetypes,22x22/actions,22x22/apps,22x22/devices,22x22/filesystems,22x22/mimetypes,32x32/actions,32x32/apps,32x32/devices,32x32/filesystems,32x32/mimetypes,48x48/actions,48x48/apps,48x48/devices,48x48/filesystems,48x48/mimetypes,64x64/actions,64x64/apps,64x64/devices,64x64/filesystems,64x64/mimetypes,128x128/actions,128x128/apps,128x128/devices,128x128/filesystems,128x128/mimetypes
[16x16/actions]
Size=16
Context=Actions
Type=Threshold
[16x16/apps]
Size=16
Context=Applications
Type=Threshold
[16x16/devices]
Size=16
Context=Devices
Type=Threshold
[16x16/filesystems]
Size=16
Context=FileSystems
Type=Threshold
[16x16/mimetypes]
Size=16
Context=MimeTypes
Type=Threshold
[22x22/actions]
Size=22
Context=Actions
Type=Threshold
[22x22/apps]
Size=22
Context=Applications
Type=Threshold
[22x22/devices]
Size=22
Context=Devices
Type=Threshold
[22x22/filesystems]
Size=22
Context=FileSystems
Type=Threshold
[22x22/mimetypes]
Size=22
Context=MimeTypes
Type=Threshold
[32x32/actions]
Size=32
Context=Actions
Type=Threshold
[32x32/apps]
Size=32
Context=Applications
Type=Threshold
[32x32/devices]
Size=32
Context=Devices
Type=Threshold
[32x32/filesystems]
Size=32
Context=FileSystems
Type=Threshold
[32x32/mimetypes]
Size=32
Context=MimeTypes
Type=Threshold
[48x48/actions]
Size=48
Context=Actions
Type=Threshold
[48x48/apps]
Size=48
Context=Applications
Type=Threshold
[48x48/devices]
Size=48
Context=Devices
Type=Threshold
[48x48/filesystems]
Size=48
Context=FileSystems
Type=Threshold
[48x48/mimetypes]
Size=48
Context=MimeTypes
Type=Threshold
[64x64/actions]
Size=64
Context=Actions
Type=Threshold
[64x64/apps]
Size=64
Context=Applications
Type=Threshold
[64x64/devices]
Size=64
Context=Devices
Type=Threshold
[64x64/filesystems]
Size=64
Context=FileSystems
Type=Threshold
[64x64/mimetypes]
Size=64
Context=MimeTypes
Type=Threshold
[128x128/actions]
Size=128
Context=Actions
Type=Threshold
[128x128/apps]
Size=128
Context=Applications
Type=Threshold
[128x128/devices]
Size=128
Context=Devices
Type=Threshold
[128x128/filesystems]
Size=128
Context=FileSystems
Type=Threshold
[128x128/mimetypes]
Size=128
Context=MimeTypes
Type=Threshold



---

