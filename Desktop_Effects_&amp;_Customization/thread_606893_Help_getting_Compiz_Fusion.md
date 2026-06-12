---
title: "Help getting Compiz Fusion?"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by SamTyson92 on 2007-11-08
Now I just got xserver-xgl and I know thats XGL but I wondered whats what because I know theres the following:
XGL
Compiz
Beryl
Compiz Fusion

And I want the one that gives me the most power to make linux look WOW

Im currently using XGL i think as I had to put xserver-xgl into the terminal and its all installed but I was wondering what I need to do to get Compiz Fusion (as thats supposedly best) and Im a n00b so easy guide please.

---

### Post by urk_nono on 2007-11-08
If you're using Feisty and have an ATI card you might want to try this:

[Installing Beryl/Compiz  Fusion]("http://ubuntuforums.org/showthread.php?t=488385&highlight=beryl+ati+radeon")

Remember to take backup of your xorg.conf incase it breaks. "**sudo dpkg-reconfigure xserver-xorg**" is always good to know by heart (saved me a few times!)

Good luck! :)

---

### Post by SamTyson92 on 2007-11-08
> **urk_nono said:**
> If you're using Feisty and have an ATI card you might want to try this:

[Installing Beryl/Compiz  Fusion]("http://ubuntuforums.org/showthread.php?t=488385&highlight=beryl+ati+radeon")

Remember to take backup of your xorg.conf incase it breaks. "**sudo dpkg-reconfigure xserver-xorg**" is always good to know by heart (saved me a few times!)

Good luck! :)


It says its all installed already so how do I add new plugins or view what plugins I have and how to use them?

---

### Post by jryprt on 2007-11-08
Here is a great guide

[http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users)

---

### Post by SamTyson92 on 2007-11-08
> **jryprt said:**
> Here is a great guide

[http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users)

Thanks I've got it sorted now!
I can't find the plug-in that when you minimize a app it burns it, I've seen it on many Compiz videos in the past and wonder how I can get it?

---

### Post by overdrank on 2007-11-08
> **SamTyson92 said:**
> Thanks I've got it sorted now!
I can't find the plug-in that when you minimize a app it burns it, I've seen it on many Compiz videos in the past and wonder how I can get it?

Hi and it is under animations in CCSM. :KS

---

### Post by SamTyson92 on 2007-11-08
> **overdrank said:**
> Hi and it is under animations in CCSM. :KS

Is the CCSM the Advanced Desktop Effects Settings?

I can't find it you see or can you tell me the default macro for it?

---

### Post by SamTyson92 on 2007-11-08
How can I get Compiz skins like the Windows Vista style one?

---

### Post by haunticious on 2007-11-08
Yes CCSM is desktop effects advanced settings .Go into the desktop effects advanced settings and the burn effect is under animations. For the vista-style skins check [www.gnome-look.org](www.gnome-look.org) for compiz skins. Once you've done this go into terminal and type sudo apt-get install emerald once you have done this there should be an emerald theme manager option under system>preferences. Here you can install and use the skins you found on gnome-look. To start emerald either press Alt+F2 or type in a terminal emerald --replace

---

