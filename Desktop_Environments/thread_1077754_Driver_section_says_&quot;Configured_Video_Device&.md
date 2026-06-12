---
title: "Driver section says &quot;Configured Video Device&quot; not matrox??"
date: 2009-02-22
forum: Desktop Environments
---

### Post by timZZ on 2009-02-22
Hi,

[Information]

Version: Ubuntu 8
Graphics Card: Matrox g45+MDHP16D
Enviroment: Gnome


I was trying to install the dual screen on my ubuntu setup and have been following this post.

[http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)

In the example the person duplicated the driver section like so.

> 
Section "Device" 
Identifier "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
Driver "ati" 
BusID "PCI:1:5:0" 
EndSection
        
Section "Device" 
Identifier "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)" Driver "ati" 
BusID "PCI:1:5:0"
EndSection


However all mine says is

> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection


Which obviously won't work.

Any clues?

Do I need to run the reconfigure first?

---

### Post by timZZ on 2009-02-22
Ok reconfigure wasn't the answer.
Am I missing a step here?

---

### Post by mcduck on 2009-02-22
The identifier is meaningless, you can use any name you want for your devices. The system detects the device based on the BusID, identifier is just a helper for the user. If you want you can call your graphics card "Jane" and use that in your configurations. ;)

The important thing is just that whatever name you use in the device section, you need to use same name when referring to that device in the Screen section.

---

