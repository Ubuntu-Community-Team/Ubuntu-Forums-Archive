---
title: "Dual Monitors Displaying Improperly"
date: 2012-10-27
forum: Desktop Environments
---

### Post by amaz1ng on 2012-10-27
So I'm having this problem here, see. Only one monitor will work correctly. That is, I cannot have two monitors enabled without one overlapping the other.

Whenever I try to reposition a display in the Displays tab, I get these two errors

"The selected configuration for displays could not be applied required virtual size does not fit available size: requested=(2646, 1024), minimum=(320, 200), maximum=(1600, 1600)"

"Failed to apply configuration: %s GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: required virtual size does not fit available size: requested=(2646, 1024), minimum=(320, 200), maximum=(1600, 1600)"

Anybody have any ideas? Thanks in advance!

Also see: [IMG]http://i.imgur.com/gzisT.jpg?1[/IMG]

---

### Post by amaz1ng on 2012-11-27
Folks, the solution that finally worked for me was editing xorg.comf. Details in keelzebub's reply here: [http://ubuntuforums.org/showthread.php?t=2073125](http://ubuntuforums.org/showthread.php?t=2073125)

---

