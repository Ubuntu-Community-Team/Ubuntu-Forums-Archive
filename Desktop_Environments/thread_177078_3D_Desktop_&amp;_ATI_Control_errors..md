---
title: "3D Desktop &amp; ATI Control errors."
date: 2006-05-15
forum: Desktop Environments
---

### Post by OpticalIllusion on 2006-05-15
I have a Dell i9300 laptop with an ATI Mobility x300 video card.  I used this wiki to learn how to install the proper ATI driver.
[http://doc.gwos.org/index.php/Install_latest_ATi_Drivers_%288.24.8%29](http://doc.gwos.org/index.php/Install_latest_ATi_Drivers_%288.24.8%29)

So, I installed 3D Desktop.
> 
sudo apt-get install 3ddesktop


It appears as if it installed correctly, but now when I enter "3ddesk" in the terminal I get this error:
> 
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)


And any time I click on the "ATI Control" under Applications I get this error:
> 
Driver does not provide the FireGL X11 extensions!
Panel components will operate only partialy.


After I Click OK it takes me to the screen, but I can't change anything.

> 
OpenGL:
Vendor:    unavailable
Renderer:    unavailable
Version:    unavailable


What's going on here?  Did I install my driver incorrectly somehow?  :confused:

---

### Post by wblancqu on 2006-05-15
Try installing ATI drivers using Method 2 of [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide").

Grtz

---

### Post by MiKuS on 2006-05-15
:whoops wrong thread](*,)

---

