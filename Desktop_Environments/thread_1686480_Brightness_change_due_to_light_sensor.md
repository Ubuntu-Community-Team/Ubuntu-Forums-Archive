---
title: "Brightness change due to light sensor"
date: 2011-02-12
forum: Desktop Environments
---

### Post by hasagar on 2011-02-12
Hi,

My lenovo ideapad U460 changes its brightness constantly. It has a ambient light sensor.
I dont know how to deactivate ambient light sensor.

I found something for ASUS laptop. But that did not work.

Please respond thanks

Platform 
Ubuntu 10.10 x86

---

### Post by Copper Bezel on 2011-02-12
Apparently this has [come up before]("http://ubuntuforums.org/showthread.php?t=1626696") but hasn't really been solved, and most of what I'm getting from Google is about the fact that the function keys for brightness won't work. The tip suggested in the thread I just linked is a rather toolshed solution of just covering the light sensor with a bit of electrical tape. The better solution would be to find and disable the control in your ACPI configuration, but that'll involve a lot of digging in text files (and some risk of mucking things up further if you change the wrong value.)

---

### Post by artemyk on 2011-06-19
I was able to fix this by booting into Windows and using the Lenovo power management settings to disable the ambient light sensor (directions at [http://forums.lenovo.com/t5/IdeaPad-Y-and-U-series-Laptops/Y560-Disable-Auto-Adjust-Screen-Brightness-ambient-light-sensor/ta-p/270494](http://forums.lenovo.com/t5/IdeaPad-Y-and-U-series-Laptops/Y560-Disable-Auto-Adjust-Screen-Brightness-ambient-light-sensor/ta-p/270494) ).  

Not sure how to do this in Ubuntu.

---

