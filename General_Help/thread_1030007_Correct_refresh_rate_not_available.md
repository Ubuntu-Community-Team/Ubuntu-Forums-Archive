---
title: "Correct refresh rate not available"
date: 2009-01-04
forum: General Help
---

### Post by Geezle on 2009-01-04
I just got myself a shiny new monitor, but the the monitor auto detection isn't quite getting it right.  I have the correct resolutions available, but I can only get a refresh rate up to 51hz, but it should be 75hz.

I know I need to set it up in xorg.conf and I've been reading about it, but I just can't seem to get my head around what I need to do.  

The monitor is a Samsung SyncMaster 953BW (specs are here[http://http://www.samsung.com/us/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS19AQWKF/XAA&fullspec=F]("http://http://www.samsung.com/us/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS19AQWKF/XAA&fullspec=F"))

If somebody could help me out with this, I'd really appreciate it.  I tried going through a tutorial on here, but I ended up kicking myself into low graphics mode.  I did use the modeline utility and came up with this:
```
 
  Horizontal Resolution:   1440 
  Vertical Resolution:      900 
  Vertical Refresh Rate:   56.00 Hz 
  Horizontal Refresh Rate: 52.15 KHz 
  Dot Clock Frequence:     95.13 MHz 

 # V-freq: 56.00 Hz  // h-freq: 52.15 KHz
 Modeline "1440x900" 95.13  1440 1488 1608 1824   900  900  902  931 

``` 
But I'm not entirely sure what to do with it.

I'm trying to get the monitor to do 1440x900 @ 75hz.

Any help would be greatly appreciated :)

---

### Post by Sef on 2009-01-04
Locked. [Duplicate Post]("http://ubuntuforums.org/showthread.php?t=1030006").

---

