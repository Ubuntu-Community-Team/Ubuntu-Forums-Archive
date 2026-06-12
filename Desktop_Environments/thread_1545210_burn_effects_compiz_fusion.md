---
title: "burn effects compiz fusion"
date: 2010-08-03
forum: Desktop Environments
---

### Post by endurance001 on 2010-08-03
Im trying to enable the burn feature in compiz fusion  so my computer can use the effects in the applications, places and systems taskbar how would I go about doing that ?

---

### Post by Zorgoth on 2010-08-03
a)

If you have not installed these packages:

sudo apt-get-install compizconfig-settings-manager compiz-fusion-plugins-extra.

Then run ccsm either with Alt-F2 - "ccsm" - <Enter> or by going to System > Preferences > CompizConfig Settings Manager.

Scroll down until you find the "Animations" icon - it is listed under "Effects."  Enable *both* it and "Animations Add-ons." (just check the checkboxes next to the icons)  Then you can edit all your effects, including burn, by clicking on the Animations icon.

---

### Post by endurance001 on 2010-08-03
I keep having to type this command in /usr/bin/compiz
 to start the program  the sudo compiz extra package is already installed ... the burn feature is not accessible

---

### Post by Zorgoth on 2010-08-04
???  I don't really understand your post.

Do you have CompizConfig Setting Manager?

If so, is Animations Add-ons enabled?

---

### Post by endurance001 on 2010-08-10
ccsm is installed
add on are enabled for animations 
 however it wasn't starting when ubuntu started so I had to use the command I post in my previous thread to start the program because ubuntu 10.04 disabled it after the upgrade from 9.10  
how do I configure the burn animation to burn when I click on Application, places, and System ??

---

### Post by Zorgoth on 2010-08-10
> **endurance001 said:**
> ccsm is installed
add on are enabled for animations 
 however it wasn't starting when ubuntu started so I had to use the command I post in my previous thread to start the program because ubuntu 10.04 disabled it after the upgrade from 9.10  
how do I configure the burn animation to burn when I click on Application, places, and System ??


Here is a screenshot of an appropriately configured ccsm > Animations:

---

### Post by endurance001 on 2010-08-21
when I enter the command in terminal user/bin/compiz this comes up 

Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

---

