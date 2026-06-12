---
title: "Visual Studio in VirtualBox"
date: 2009-03-06
forum: General Help
---

### Post by specterunseen on 2009-03-06
**Problem #1 **
Has anyone successfully done this? I've read for hours online attempting to get it to work. The virtualbox forum hasn't been very helpful. 

See that posting for full details. The error possibly causing this is the fact I can't change the installation location. I can't figure out how to mount another VDI drive inside the VB, but regardless, it still won't install on the "c:/" that is provided, why?!? Doesn't even start the installation. 
 
[http://forums.virtualbox.org/viewtopic.php?f=7&t=15094](http://forums.virtualbox.org/viewtopic.php?f=7&t=15094)
> You cannot change the location of the component or its subcomponents because the component has already been stored in a different location, or it has a dependency on a file already stored in a different location.

The following programs are causing vertical integration to occur:


{A4418082-E601-3954-805B-D56A2B50EC8B} 

To change the file path, you must uninstall the programs listed above and reinstall them in the location where you want to store the files shared with Visual Studio. 


**Problem # 2**
Mentioned as well in that link. I have three screens, I can't seem to get VB to work with the RDP. Anyone who has experince with this that can help? I'm about to give up with using Ubuntu primarily because of this, though I REALLY want to stick it out. School makes my time limited, and despite hours of googling I'm no closer to finally getting this to work. Help please? :)

---

### Post by specterunseen on 2009-03-06
btw, the error generated is: 
> EventType : visualstudio8setup P1 : 10861 
P2 : 9.0.30729.01_orcas_x86_net P3 : msi P4 : inst P5 : f P6 : -
P7 : - P8 : 1601 P9 : - P10 : 



C:\DOCUME~1\Sheldon\LOCALS~1\Temp\WLFC.tmp
C:\DOCUME~1\Sheldon\LOCALS~1\Temp\SDBD.tmp
C:\DOCUME~1\Sheldon\LOCALS~1\Temp\VSW0\VSSWMSISumm ary.txt
C:\DOCUME~1\Sheldon\LOCALS~1\Temp\VSW0\VSSWMSIFail Info.txt
<NoFiles> 

I think the problem has to do with the installation issue not allowing the installation location to change, has something to do with each other.

---

