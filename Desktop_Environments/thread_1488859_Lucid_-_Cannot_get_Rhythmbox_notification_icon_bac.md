---
title: "Lucid - Cannot get Rhythmbox notification icon back"
date: 2010-05-20
forum: Desktop Environments
---

### Post by mk1w86 on 2010-05-20
I have a machine running Ubuntu 10.04 and I accidentally removed the Rhythmbox icon in the notification area by right clicking it and I think I must have selected remove or something.

The problem is I cannot seem to get it back and it is enabled under the Plugins section of Rhythmbox. :confused:

---

### Post by 3Miro on 2010-05-20
Try to right-click on the notification panel and to bring up Properties or something like that. Under XFCE I can select apps that I do not want to appear in that area.

Another option is to check the Rhythm box itself. It will have a notification icon settings somewhere.

(sorry for not being more helpful)

---

### Post by moongia on 2010-05-20
> **mk1w86 said:**
> I have a machine running Ubuntu 10.04 and I accidentally removed the Rhythmbox icon in the notification area by right clicking it and I think I must have selected remove or something.

The problem is I cannot seem to get it back and it is enabled under the Plugins section of Rhythmbox. :confused:

the plugin is "status icon",,if you dont see it still,you may have removed the indicator applet..right click and add it back..you may need to log out and back..hope this helps.

---

### Post by coslo on 2010-05-20
As pointed out by moongia you probably removed the Indicator Applet. If you want to get it back, right click on the upper panel, then Add to panel > Indicator Applet. However, you can also live without it: just reboot, open Rhythmbox and you should see the status icon (provided you keep the status icon plugin enabled in Rhythmbox). Actually I disabled the Indicator Applet for the moment, as I find it confusing.

---

### Post by mk1w86 on 2010-05-21
A reboot seemed to fix the problem. :)

I knew I should have tried that first, I'm just so used to changes made in Gnome taking effect immediately. ](*,)

---

### Post by lindenbranch on 2010-10-04
> **moongia said:**
> the plugin is "status icon"...hope this helps.
Yes, that helped a lot.  Apparently the configuration for this plugin changed when I upgraded from 10.04 to 10.10.  Thanks.

---

### Post by svenskmand on 2010-10-11
> **lindenbranch said:**
> Yes, that helped a lot.  Apparently the configuration for this plugin changed when I upgraded from 10.04 to 10.10.  Thanks.
The exact same thing happened for me :S, after upgrading to 10.10 the indicator symbol disappeared, but going to Rhythmbox plugins section and changing it helped :)

---

