---
title: "Xubuntu 9.04. Splash Screen"
date: 2010-09-27
forum: Desktop Environments
---

### Post by 55tptag on 2010-09-27
Hi,

I like the artwork used in Xubuntu 9.04 for the splash screen.  So, I searched my Xubuntu 9.04 install for it. But, can't find it.

Does anyone know where it's located?  Picture of splash screen is attached to this post.

I've done the following two searches of the file system but no luck:
# find / -iname "*xfce*.png"
# find / -iname "*xubun*.png"

Thank you for your help.

---

### Post by 55tptag on 2010-10-07
Is it called the splash screen?

---

### Post by Dustin2128 on 2010-10-07
> **55tptag said:**
> Is it called the splash screen?
probably something more like login screen background. That screen looks amazing though, I'm going to start looking for it.

---

### Post by Jose Catre-Vandis on 2010-10-07
Try here

usr/share/xfce4/backdrops

---

### Post by 55tptag on 2010-10-09
> **Jose Catre-Vandis said:**
> Try here

usr/share/xfce4/backdrops

Thanks.  I checked there.  But it wasn't in that directory.

I also looked in:
/usr/share/pixmaps/
/usr/share/app-install/icons/
/usr/share/metacity/icons/
/usr/share/icons/

And finally found it in:
/usr/share/gdm/themes/xubuntu/jaunty-gdm.png

---

