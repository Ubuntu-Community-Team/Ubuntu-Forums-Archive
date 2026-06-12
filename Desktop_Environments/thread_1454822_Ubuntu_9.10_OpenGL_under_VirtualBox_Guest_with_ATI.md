---
title: "Ubuntu 9.10 OpenGL under VirtualBox Guest with ATI Radeon"
date: 2010-04-15
forum: Desktop Environments
---

### Post by autolux on 2010-04-15
hi there,

seem to be experiencing a catch22 situation here.

I'm running Windows 7 x64bit host, QuadCore/Radeon 4850 with latest drivers, with VirtualBox 3.1.6 running a Ubuntu 9.10 x86 guest.

now first thing I do after fresh Ubuntu install, is to install VirtualBox Guest Additions. Then onto installing cairo-dock, now this works fine, I'm able to run it as normal in OpenGL mode without issues, looks great etc.

however, for compiz to be enabled, I need to shutdown the guest, and enable "3d acceleration" for the guest O/S under VirtualBox's settings for the guest.

once this is done, I'm able to use "effects" under "System/Preferences/Appearance" and compiz works great, but OpenGL cairo-dock will no longer run.

running either /usr/sbin/cairo-dock or fglrxinfo returns the error:
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Segmentation fault

I've spent quite a few hours searching around for answers and tinkering without luck. Also, I thought it may just be an ATI thing, but I've got basically the same setup only with an Nvidia 9600GT card also on another machine, same problem... 

so far I've installed the latest ATI catalyst under the guest OS, which was pointless as there is no physical card accessible for the guest so it doesn't run. I've also installed the ATI X-org driver from the Ubuntu Software Manager, no change. 

Doesn't quite make sense to me that compiz will be fine with all it's 3d accelerated goodness, but openGL cairo-dock doesnt work.

can somebody fill me in on the correct usage for OpenGL to work under this situation?

---

### Post by autolux on 2010-04-18
eh nobody?

cairo OpenGL works without guest additions, with guest additions, compiz works but no cairo OpenGL.

---

