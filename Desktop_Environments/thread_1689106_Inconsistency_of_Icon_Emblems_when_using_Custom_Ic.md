---
title: "Inconsistency of Icon Emblems when using Custom Icon Theme"
date: 2011-02-16
forum: Desktop Environments
---

### Post by ryandi on 2011-02-16
I have recently installed Faenza icon theme and just began to notice the inconsistency of icon emblems being displayed by compiz.

Attached image shows the emblems of Chromium, Nautilus and Comix are that of the default icons, while Empathy and CompizConfigSettingsManager displayed the custom icon correctly. The dock displays all apps' icons correctly though.

The issue does not occur exclusively to Application Switcher (Alt+Tab), it also occurs with Scale (Super+W), Shift Switcher (Super+Tab).

Any help with correcting this issue is appreciated.

---

### Post by Frogs Hair on 2011-02-16
Hi and Welcome !
Have you checked to see if the emblems are simply drawn differently than the rest of the icons . Some icon sets include overlay icons that are not the same as those shown on the menu or dock.

If you set your dock to display overlay icons this difference is often visible . Emblems are usually pictures that are added to folder icons for identification and found by clicking on a folder and going into properties > emblems .

---

### Post by ryandi on 2011-02-16
Hello Frogs Hair, thanks for the support! I apologize for confusing between emblem and overlay icons.

If these icon sets include overlay icons, where could they be stored in order for compiz to read them? I have checked the subfolders of /usr/share/icons/Faenza/apps and the correct pngs are present for them (same to those shown on menu/dock)

---

### Post by Frogs Hair on 2011-02-16
If you are using the compiz applet from your dock settings it comes with its own icon and will look different than the icon included in your set . By the looks of it you may be using GlX/ Cairo dock , when I used GLX it was posibble to change some of the applet Icons but I was never able to change the Compiz icon because of the additional functions it had such as expo.
 
If you want things to look the same , one way is to add launchers in place of applets . When you open a program and the icon appears on the dock add it as a launcher. If you add a Compiz short cut to the dock it will be just that and won't function like the applet.

---

### Post by Frogs Hair on 2011-02-16
I should add that all the applet icons may be different than the set you are using , so when overlay is used the primary icon displayed on the dock is the applet icon and the overlayed icon comes from your set. This is why they look different.

---

### Post by ryandi on 2011-02-16
I should have removed the compiz applet before taking print screen, my bad for confusing you.

I wasn't worried about the CCSM's overlay icon, in fact it behaved correctly compared to others like Chromium, Comix and Nautilus (and also Chrome, Firefox).

Chromium's overlay icon should look like the app left-most in the dock. Comix's should look like the fourth and nautilus' should look like the ninth. I'm wondering why some of the overlay icons do not obey the custom icon installed? Are they cached or something?

Edit: Take a look at Empathy's overlay icon. It follows that of the custom icon theme

---

### Post by Frogs Hair on 2011-02-16
There is a difference between the  icon that comes with your dock applet and the icon that comes with your Faenza set.

If you use the dock applet there will be a difference . If you add an application launcher via drag and drop then the icons should match those on your menu.

---

### Post by ryandi on 2011-02-17
It seems that we are still talking about different things. When I mention compiz, I talk about the compositing window manager. So I was asking about how compiz (the compositing window manager) reads the overlay icons for every app; not why the compiz applet has a different icon to itself. I have this OCD of getting inconsistent thing right, but I guess I could live with this one. Thanks for the help and sorry for confusing you by giving a bad example. Marked as solved.

---

### Post by Copper Bezel on 2011-02-17
I'm thinking that with some branded software, it seems that Compiz uses the default icon. Using any of the switcher plugins on a minimized window does this, too.

That default branding icon shows up in other places, too. If you use Avant Window Navigator, one of the options for displaying a running pinned app is called "overlay application icon," and the default icon displays over the custom one. Talk about an uncomfortable juxtaposition for the OCD-inclined. = )

---

