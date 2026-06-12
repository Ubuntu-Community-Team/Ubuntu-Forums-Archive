---
title: "Gnome and KDE mouse settings conflict"
date: 2007-06-22
forum: Desktop Environments
---

### Post by nym.null on 2007-06-22
While I'm reasonably happy with Gnome, I find that I'm using KDE apps more often and want to explore using KDE desktop (again).   I've installed kde-desktop and can easily switch from Gnome to KDE -- except for one apparent problem: incompatible mouse settings.  And I have to maintain Gnome for other users on this box.

Using a [ Logitech LX7 ]("http://www.logitech.com/index.cfm/mice_pointers/mice/devices/152&cl=ca,envv")mouse I am able to use all 9 'buttons' as I like (including L/R tilt and page forward/back) through simple config in xorg.conf.  This works fine in Gnome.  

When I startup KDE I expected to have the same settings (it's from the same xorg.conf, right?) but have some weirdness to deal with, as outlined below.
[B]
Observed problems[/B] ```

		In Gnome	|---------In KDE---------|
				Firefox:	Konqueror:
Left click	= Left click	OK		OK
Right click	= Right click	OK		OK
Middle click	= Paste		OK		OK
Left tilt	= Scroll left	OK		OK
Right tilt	= Scroll right	OK		OK

Scroll down	= 		Forward		Scroll right
Scroll up	= 		Back		Scroll left
Back		= 		Scroll down	Scroll down
Forward		= 		Scroll up	Scroll up
```

If I make changes to xorg.conf, the weirdness/problem is just transferred to Gnome.  

Is there a method to make mouse control changes specific to KDE such that Gnome is left untouched (or vice-versa), or can someone suggest a utility that can be configured to give the same results whether using Gnome or KDE?

[btnx]("http://ubuntuforums.org/showthread.php?t=455656")? 
imwheel?

All help is greatly appreciated.

---

