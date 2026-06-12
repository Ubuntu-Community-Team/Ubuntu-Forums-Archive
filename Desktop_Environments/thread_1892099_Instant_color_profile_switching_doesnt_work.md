---
title: "Instant color profile switching doesnt work"
date: 2011-12-07
forum: Desktop Environments
---

### Post by taphos on 2011-12-07
When I switch monitor color profile in Unity color management tool (Seems it is inherited from gnome3 project) nothing happens, i see no changes on the screen :(

I can see the profile is changed in colord
> 
$ colormgr get-devices


And my driver supports xrandr version 1.3
> 
$ xrandr -v
xrandr program version       1.3.5
Server reports RandR version 1.3


So what could be the problem?
Should the color profile be switched on the fly at all? or should i reboot? or relogin?

I am very happy that ubuntu now supports color management as every good os should, but it would be even beter if it would work :)
Any help would be very much appreciated.

---

