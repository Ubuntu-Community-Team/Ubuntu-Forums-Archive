---
title: "Can not start X automatically"
date: 2010-06-07
forum: Desktop Environments
---

### Post by rudolfl on 2010-06-07
Hi, all
Before you ask -- I have looked through the forums and  searched Google and tried suggestions found.
I run Ubuntu 10.04 on  Toshiba Tecra laptop with NVIDIA video card.

Everything used to  work just great with NVIDIA driver supplied with UBUNTU. Recently,  however, something has happened and my boot up procedure now is as  follow:
Start PC and select OS to load (as before)
OS starts to  load and probes the screen and video hardware
I get message "UBUNTU  is running in low graphics mode...." I press Ok and get menu where I  select "Restart X"

I get another box with message "Stand by one  minute while the display restarts...", 100% completed progress bar and  OK button. This box stays up forever until I press OK

I am  getting console prompt, log in and execute 'startx'
X loads and run  OK, with 3D acceleration, visual effects, etc...


Looking at  the Xorg log fail, I can see error: "Failed to initialize GLX extension  (Compatible NVIDIA X driver not found)".

If system can not find  NVIDIA driver, how come manual start of X server works fine????

Last  thing I remember doing before problem occured is to try and install  MythTV. That was deleted since, but problem is still there. MythTV may  or may not be related to this issue, as laptop is not restarted that  often, so problem could be there for awhile and I did not know about it.

Anyway,  if someone has any ideas, please let me know.

Thanks,
Rudolf

---

### Post by tim48134 on 2010-06-08
Hmm.. Have you tried selecting "Reconfigure Graphics" (or something like  that) at the prompt that said Ubuntu was running in low-graphics mode?  That would try to configure X with the graphics drivers you currently  have. That message about GLX has to do with OpenGL. On a system with the  open source nVidia drivers, the GL implementation is Mesa (this is the  default). Xorg will still work, even without the open source nVidia drivers. It does this by defaulting to VESA, which is the generic driver for X. There is a proprietary, yet still cost-free, driver available  from nVidia, which includes nVidia's version of OpenGL as well. You can  get it from System->Administration->Hardware Drivers, or from  "sudo apt-get install nvidia-*". You must replace the * with 'current'  for GeForce 6 series or higher, '173' for GeForce 5-9, or '96' for  GeForce series 2 (except for GeForce2 GTS/GeForce2 Pro, GeForce2 Ti and  GeForce2 Ultra) to Geforce series 7. Hope this helps at least a little!

---

### Post by rudolfl on 2010-06-08
Thanks for the reply.
i did try to reconfigure graphics -- no luck.
I did not try nVidia driver, but I did try to switch between 173 and 96 without success. Driver obviously works since I can start X manually, but why did it stop detecting it on startup? 

Rudolf

---

### Post by resolv_25 on 2010-06-09
Uf, not happy to see this.
I had quite some trouble with Nvidia driver with previous version of Ubuntu, and I'm planning one of these days to upgrade it on v.10.04.
Try to take a look on this manual:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Install_Latest_Nvidia.2FATI_drivers)
( option: Reconfigure xserver-xorg on the same page )
or this: [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
or drivers from nvidia.com : [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

As mentioned in manual, it is wise to make a backup of */etc/X11/xorg.conf*
before installing a new driver.

---

