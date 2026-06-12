---
title: "Software OpenGL in Xorg 6.8"
date: 2005-01-28
forum: Desktop Environments
---

### Post by Hec on 2005-01-28
Hi everybody! This is my first post in the forum, so I'll present myself. I'm an ex-gentoo users that tried ubuntu and felt in love inmediatly. I use it in my laptop, and everything's fine but Open GL. Xorg and XFree always reverts to software Open GL. It worked in gentoo, so I know the chip is capable of. I'll post my Xorg config: 

#Modules config
Section "Module"

#	Load  "GLcore"
	Load  "bitmap"
	Load  "dbe"
	Subsection "extmod"
  		Option "omit xfree86-dga"  
	EndSubSection 
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "speedo"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

#Adapter config
Section "Device"
	Identifier  "Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver      "i810"
#     VideoRam    131072	
	Option "XaaNoOffscreenPixmaps" "True"	
	BusID       "PCI:0:2:0"
EndSection

#DRI
Section "DRI"
	Mode         0666
EndSection

DRI it's working fine, and the problem it's not related to XaaNoOffscreenPixmaps, as it worked in gentoo. Any help would be apreciated.

Thanks in advance

Edit: Solved with the new package. Thankyou all for your answers.

---

