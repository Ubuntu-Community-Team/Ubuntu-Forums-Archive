---
title: "Hz monitor....."
date: 2007-04-27
forum: Desktop Environments
---

### Post by pisio on 2007-04-27
Hi for all.
I have a problem with Hz.
In Windows my monitor worked in 80~100Hz,but in Ubuntu 6,10 and Ubuntu7 working in 60 Hz.
How to make a monitor work in 80~100Hz.
You can look a 
[/etc/X11/xorg.conf  <CLICK HERE>]("http://usalug.org/pastebin/pastebin.php?show=6399")
[-o< [-o< [-o< [-o< [-o<
Thanks
Edit://
In System >>> Preferences >>> Screen Resolution 
I don't  change the Hz.
In thise menu have only 60Hz

---

### Post by sisco311 on 2007-04-27
[howto]("http://ubuntuforums.org/showthread.php?t=76387")
or google for your monitors horizontal and vertical scan range and edit it  in your xorg.conf file
> #
Section "Monitor"
        Identifier      "Generic Monitor"
        Option    "DPMS"
        [B]HorizSync       28-50
        VertRefresh     43-60[/B]
EndSection

---

### Post by sisco311 on 2007-04-27
and install the nvidia driver
in 7.04 System ->> Administration ->> Restricted Drivers Manager
[or use the envy scrip for both versions (6.10, 7.04)]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by pisio on 2007-04-27
> **sisco311 said:**
> [howto]("http://ubuntuforums.org/showthread.php?t=76387")
or google for your monitors horizontal and vertical scan range and edit it  in your xorg.conf file

I write :
[PHP]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-85
EndSection[/PHP]
And now my monitor work  with 85Hz
Thanks To two as well .

---

