---
title: "Pan newsreader stopped working"
date: 2009-05-01
forum: General Help
---

### Post by David D. on 2009-05-01
I am using an HP dv7 laptop with Ubuntu 9.04.  Pan started dropping its connection to the internet, then froze, so I tried to exit the program.  Upon trying to exit I had to "force quit".  Now Pan will not launch from Applications.  When I attempt to launch Pan from the Terminal, I get "Segmentation fault".  I have tried a complete reinstall, a complete removal then reinstall.  When I tried using Terminal to move and rename the configuration folder for Pan, it said no such file or directory exists.  Does anyone have any ideas for what else can be done?

---

### Post by David D. on 2009-05-02
Bump.  Any ideas anyone?

---

### Post by DeMus on 2009-05-02
> **David D. said:**
> I am using an HP dv7 laptop with Ubuntu 9.04.  Pan started dropping its connection to the internet, then froze, so I tried to exit the program.  Upon trying to exit I had to "force quit".  Now Pan will not launch from Applications.  When I attempt to launch Pan from the Terminal, I get "Segmentation fault".  I have tried a complete reinstall, a complete removal then reinstall.  When I tried using Terminal to move and rename the configuration folder for Pan, it said no such file or directory exists.  Does anyone have any ideas for what else can be done?

With the configuration folder you mean: .pan2 ?
After the complete uninstall you can safely remove this folder and re-install pan again. Normally spoken it should work again, but then again what is normal?

---

### Post by David D. on 2009-05-02
Update - I can now launch Pan from a terminal using gksudo.  The icon for Pan Newsreader located in "Applications - Internet" will not launch Pan.  My problem is now making the program launch from the icon.  I do note that in the properties for the icon that for Pan the command is listed as "pan" while for Firefox the command is listed as "firefox %u".  I have tried adding " %u" to pan with no success.  How do I get the icon working properly again?

---

### Post by David Raleigh Arnold on 2010-09-01
> **David D. said:**
> Update - I can now launch Pan from a terminal using gksudo.  The icon for Pan Newsreader located in "Applications - Internet" will not launch Pan.  My problem is now making the program launch from the icon.  I do note that in the properties for the icon that for Pan the command is listed as "pan" while for Firefox the command is listed as "firefox %u".  I have tried adding " %u" to pan with no success.  How do I get the icon working properly again?

I saw another thread on this topic and started deleting the contents of directories
and files in the .pan2 directory. Deleting the contents of "groups" did the trick,
and I still had my gmane preferred groups. My ISP stopped providing usenet,
so gmane is now all that I use pan for. You do not want to continue launching
pan as root. Since it works when launched as root, the problem must be
the processing of whatever is in your .pan2 directory, because that is the
difference between the root instance and your instance. Regards, daveA

---

