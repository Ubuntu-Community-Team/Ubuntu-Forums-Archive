---
title: "Help im new with Ubuntu!"
date: 2008-01-31
forum: Desktop Effects &amp; Customization
---

### Post by lamebat on 2008-01-31
**Hi:**
I currently run the newest version of Ubuntu (Ubuntu 7.10).
I want to install all the plug-ins that is used in this video: [http://www.youtube.com/v/bvnQE1EAEZY&rel=1]("http://www.youtube.com/v/bvnQE1EAEZY&rel=1")
I find it handy to have them when am editing my photos in Photoshop and Illustrator, so please can some one help me?

**PS:This is my specs.**
*I've got a NVIDIA Quadro NVS 140M, 1,8GHz Core 2 Duo CPU and 2Gb of RAM:*

---

### Post by overdrank on 2008-01-31
> **lamebat said:**
> **Hi:**
I currently run the newest version of Ubuntu (Ubuntu 7.10).
I want to install all the plug-ins that is used in this video: [http://www.youtube.com/v/bvnQE1EAEZY&rel=1]("http://www.youtube.com/v/bvnQE1EAEZY&rel=1")
I find it handy to have them when am editing my photos in Photoshop and Illustrator, so please can some one help me?

**PS:This is my specs.**
*I've got a NVIDIA Quadro NVS 140M, 1,8GHz Core 2 Duo CPU and 2Gb of RAM:*

HI and welcome, are you speaking of compiz? It is installed by default on Gutsy. You enable the effect under system, administration, appearance. The visual tab. you can use this command to install the manager
```
sudo apt-get install compizconfig-settings-manager
```
Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also make sure the rotate cube box is checked. If you are speaking of the dock at the bottom of the screen I believe that is AWN

---

### Post by lamebat on 2008-02-01
Thanks for the help :)

:confused: And by the way, i have som new problems at my "older" pc:
When I try to enable *Graphic Card* in *Restricted Drivers*, I get this message:
> The software source for the package

   nvidia-glx-new

 is not enabled.

How do i enable 'nvidia-glx-new'?

I have a NVIDIA GeForce Go 6600, graphic card. :popcorn:

---

### Post by Tenken on 2008-02-01
There should be a check box next to the driver name that allows you to enable it.  After you enable it you will be asked to reboot for the changes to take affect.

---

### Post by lamebat on 2008-02-01
When i enter the *>Resticted Drivers* i only have one object i can enable, and thats the graphics driver. after I've done that i get a pop up that says Enable or cancel, an d after I've   done that i get the error:
> The software source for the package

   nvidia-glx-new

 is not enabled.

---

### Post by Tatty on 2008-02-06
Go to System->Administration->Software Sources.  

Make sure that all of the options are checked, then try again.

---

