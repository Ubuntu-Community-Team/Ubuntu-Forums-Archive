---
title: "Unity Settings Background is Transparent"
date: 2014-03-04
forum: Desktop Environments
---

### Post by travis-r-allen on 2014-03-04
I am using Ubuntu 13.10 with the Gnome3 PPA installed for the latest network-manager, etc.
When I open the Settings app the background of all sub-pages (Appearance, etc) are transparent. I can see through to the underlying application. See the screenshot I attached below.

[ATTACH=CONFIG]250868[/ATTACH]

I found one other person with this problem but they fixed it by purging the Gnome3 PPA and downgrading. Does anyone know what I can do to fix this?

---

### Post by Portaro on 2014-03-05
I think this is a problem on the theme config.
I dont have any idea , i think this can be made by  a compiz option but is strange that occurs when you open gnome-settings.

---

### Post by travis-r-allen on 2014-03-05
Yea I've only noticed it with the Settings app. I'm a long time KDE guy, how do I play with the compiz theme settings on Unity?

---

### Post by Portaro on 2014-03-06
you can easy manage settings of compiz by ccsm ->

$ ccsm 

open the settings manager by terminal launch.

And you have a GUI method a package called - compiz-settings-manager and fusion icon, search for this packages on synaptic for example.

---

### Post by 3rdalbum on 2014-03-08
It looks like this has been purposely done by the developers with RGBA, albeit they have set the Alpha too high so the window background is fully transparent.

If you look at System Monitor you will notice something similar. Semitransparent window backgrounds.

Keep your PPA up to date and the developers will probably issue a bug fix to turn the transparency down to a reasonable level..

This is NOT anything to do with Compiz. Compiz would make the whole window transparent, not just the background.

---

### Post by Ahmed_Matar on 2015-02-05
I had the same issue, solved it by 

[COLOR=#333333][FONT=UbuntuRegular]sudo apt-get remove gnome-settings-daemon[/FONT][/COLOR]

---

### Post by giannamelo on 2015-06-19
> **Ahmed_Matar said:**
> I had the same issue, solved it by 

[COLOR=#333333][FONT=UbuntuRegular]sudo apt-get remove gnome-settings-daemon[/FONT][/COLOR]
Thanks!
You solved my issue!

---

