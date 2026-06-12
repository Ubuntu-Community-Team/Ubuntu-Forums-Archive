---
title: "Fluxbox on Laptop"
date: 2008-06-05
forum: Debian
---

### Post by Shakey_Jake33 on 2008-06-05
I'm getting a Dell m1330 in a few days, and intend to install Debian Testing.  But I'm going to install no DE, and install fluxbox instead.  Sounds good... But I'm pretty sure GNOME has all sorts of power management features, which I don't know how to enable in fluxbox. I know when installing Debian, there is an option to install Laptop Applications.

I guess what I'm trying to say it, I want a Debian Testing Fluxbox install, can someone inform me of any specific stuff/apps/etc I need to make sure fluxbox is correctly managing power usage etc?

Thanks

---

### Post by p_quarles on 2008-06-06
Select the "laptop" task during the installation process, and basic power saving features (such as skipping fsck when on battery power) will be installed. 

The big, important thing that you will need to do yourself is installing powernowd, which manages CPU scaling for most modern PCs. This can be installed from the main repository, and the man page gives an adequate rundown of the setup steps.

---

### Post by Shakey_Jake33 on 2008-06-08
Thanks, I'll be sure to install powernowd.  Does the laptops tasks (that are installed if selected on installation) run automatically, or do they need to be manually enabled once installed?

---

