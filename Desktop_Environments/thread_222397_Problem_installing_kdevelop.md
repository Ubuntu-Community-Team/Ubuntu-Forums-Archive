---
title: "Problem installing kdevelop"
date: 2006-07-24
forum: Desktop Environments
---

### Post by ionophore on 2006-07-24
Hey everyone,

I'm having trouble installing kdevelop (from the repositories).  Everything downloads and installs fine according to dpkg, but a menu entry is not made for kdevelop on the K menu.  When I try to start it from the command line by typing "kdevelop3" I get an error message printed to the console that says this:

------------
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype KDevelop/Plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KDevelop/Plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KDevelop/Plugin not found
---------

In adition, i get a graphical text box message pop up that says:

----------
Unable to find plugins.  kdevelop will not work properly!

Please make sure that kdevelop is installed in your KDE directory, otherwise you will have to add kdevelop's installation path to the environment variable KDEDIRS and run kbuildsycoca.  Restart kdevelop afterwards. 

...
----------

After clicking Ok to this message kdevelop opens but it is clearly pretty non-functional.  I have tried uninstalling/reinstalling.  So I guess I have 2 questions:

1)  Does anyone know what the problem here is?
2)  If not, where is the KDEDIRS variable set (ie, in what text file) so that i can mess with it?

Thanks,

-Ben

---

