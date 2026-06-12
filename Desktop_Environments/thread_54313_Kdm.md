---
title: "Kdm"
date: 2005-08-04
forum: Desktop Environments
---

### Post by kap42 on 2005-08-04
I've tried to use kcontrol to change the settings of KDM. But no matter how I try, KDM will use the "standard" theme (which is butt ugly and not very user friendly). Mainly I want to enable the user images, which makes it much easier for the kids to login.

---

### Post by subzero2000 on 2005-08-04
[QUOTE=kap42]I've tried to use kcontrol to change the settings of KDM. But no matter how I try, KDM will use the "standard" theme (which is butt ugly and not very user friendly). Mainly I want to enable the user images, which makes it much easier for the kids to login.[/QUOTE]

Just figured this one out for myself yesterday. KDM (as of 3.4, it appears) supports themes, apparently similar to the way it is done in GDM (don't use GDM, so I don't know for sure). The problem is, there is no stock KDE Control Panel that supports managing themes for KDM. There are two ways that I know of to deal with this:

1) In /etc/kde3/kdm/kdmrc, you will find the following set:
[X-*-Greeter]
UseTheme=true

Change UseTheme=false and this should allow you to control KDM via the Login Manager.

2) Download, compile from source and install the KDM Theme Manager, found at 
[http://www.kde-look.org/content/show.php?content=22120](http://www.kde-look.org/content/show.php?content=22120). This will allow you to manage and turn on/off the use of KDM Themes.

The other issue you will likely encounter is with KSplash, which also uses themes, for which there is a manager in the Control Panel, but the KSplash themes don't seem to be as configurable as the ones in KDM.

HTH

---

### Post by kap42 on 2005-08-04
[QUOTE=subzero2000]Change UseTheme=false and this should allow you to control KDM via the Login Manager.
[/QUOTE]
That did the trick. Thanks a lot!

---

### Post by daller on 2005-08-05
...Well, what works???

- All it did here, was making everything ugly!

...Is it possible to make the greeter look like the greeter in Windows XP? (Showing all users as icons, and names)

...I fixed it back in my Debian-days, but I forgot what I did! :) 

If Kdm can manage this out-of-the-box - What about other display managers?

---

### Post by JLTB on 2005-08-06
I just went in and hacked the origianl kubuntu theme (does this make me lazy?).

Anyway, the files are located under /usr/share/apps/kdm/themes .  It's all quite self explanitory, I just tweaked the files under kubuntu (replaced some images edited the xml stuff), got a nice dual monitor wall paper (no skewed image :)) and moved the login box out of the center of the screen.

Oh, I'm using KDE 3.4.2 and I didn't have problems changing the theme (later i undid my hack and made my own theme).

GL

---

### Post by WMCoolmon on 2005-09-16
I tried this, but am getting:
> checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
I've checked for xorg includes but all that came up in a search was xorg-common. I've installed build-essential. Is there anything else I can do to get it working?

---

