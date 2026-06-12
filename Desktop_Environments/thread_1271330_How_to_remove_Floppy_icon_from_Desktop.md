---
title: "How to remove Floppy icon from Desktop ?"
date: 2009-09-20
forum: Desktop Environments
---

### Post by sunchiqua on 2009-09-20
I'll keep it short and let you re-read the title .. 
The problem is that I can't seem to find a way to remove Floppy icon from my Desktop ( removed from fstab .. still nothing ).
[B]
/etc/fstab[/B]:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7bdcd49c-3108-4691-8a95-952381021bb9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=af0625ea-6227-4eba-9f05-03175a7ee6a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Any ideas ?

---

### Post by FuturePusher on 2009-09-20
EDIT: This most likely only has effect with Nautilus, which I don't think is the default in XFCE.. but installable ;)

That probably happens because "external media devices" are really handled by HAL, which in turn keeps **mtab** updated, which finally Gnome/Nautilus checks to know what "external media devices" to list on the desktop (along with the "fixed media devices" it gets from fstab or via HAL).

Phew.. that info got extensive... :)

I'd suggest You go to "/apps/nautilus/desktop" in "Gnome Config Editor" (run "gconf-editor", search for it in Synaptic and install if not installed)...
and there You turn off "volumes_visible" (uncheck checkbox).
And if You want a "Computer" icon to appear, as a quick way to "dig into" Your drives instead of having drives "spontaneously" clutter Your desktop, check the "computer_icon_visible".

If You still DO want _certain_ drives to always be on the desktop, You can manually set up programstarters with this as the command (no quotes): "nautilus file:///media/floppy" or "nautilus file:///media/AnotherOfYourExistingMounts"... (and change the starters' icons to something nicer).

---

### Post by sunchiqua on 2009-09-21
[LIST=1]
[*]XFCE is not Gnome ( no gconfig-editor )
[*]XFCE default file manager is Thunar ( not Nautilus )
[*]Problem still not solved .. :(
[/LIST]

---

### Post by FuturePusher on 2009-09-21
You're absolutely right, as I've seen now that I've looked into it briefly...

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=305910](http://ubuntuforums.org/showthread.php?t=305910)

..and more specifically this Wiki it links to... ;)
[http://idesk.sourceforge.net/wiki/index.php/Main_Page](http://idesk.sourceforge.net/wiki/index.php/Main_Page)

In XFCE, the filemanager Thunar apparently does NOT handle the desktop icons, but instead, You most likely have Idesk installed.
In that case, according to [http://idesk.sourceforge.net/wiki/index.php/Idesk-usage](http://idesk.sourceforge.net/wiki/index.php/Idesk-usage), You should at least be able to manually edit Your "~/.ideskrc" ("~"="/home/YourUsername"), look for the "table Icon" entries in there, especially any with "floppy"/similar @ "Caption:"...

In any case, You need to find out exactly what's responsible for putting the icons on the desktop, and as I wrote: my guesstimate is that it's "Idesk" for You, as really nothing else in XFCE seems to handle it by default.

Good luck with it, hoping this helped.

---

