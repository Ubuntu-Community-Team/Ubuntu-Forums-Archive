---
title: "How can i Change Ubuntu 12.04 start menu icon gnome classic..."
date: 2013-04-18
forum: Desktop Environments
---

### Post by thisislinuxdj on 2013-04-18
Making an ubuntu 12.04 based linux os. i have ubuntu gnome classic installed! methods online i found are only for actuall debian gnome! tried them and did not work. also wondering how i could get dvds to work????? tried your guys steps and cannot find one codec in ubuntu software center. cannot find (**libdvdcss2). thanks pic of what i would like to change!**[ATTACH=CONFIG]241519[/ATTACH] pic here! thanks for support! :KS

---

### Post by Baldrick_NZ on 2013-04-19
> **thisislinuxdj said:**
> Making an ubuntu 12.04 based linux os. i have ubuntu gnome classic installed! methods online i found are only for actuall debian gnome! tried them and did not work. also wondering how i could get dvds to work????? tried your guys steps and cannot find one codec in ubuntu software center. cannot find (**libdvdcss2). thanks pic of what i would like to change!**[ATTACH=CONFIG]241519[/ATTACH] pic here! thanks for support! :KS

With regard to DVD playback:
Install libdvdread4 from the Ubuntu repo. To install, run the following command in terminl
```
sudo apt-get install libdvdread4
```
Once fully installed, run the command below
```
sudo /user/share/doc/libdvdread4/install-css.sh
```
Now you should be able to insert & play a DVD using Totem or VLC.

libdvdcss2 has been replaced by libdvdread4. You can still get libdvdcss2, but you need to enable the medibuntu PPA to get it.

Getting into Gnome fallback:
log out, and when you log back in, instead of choosing 'Ubuntu' click the ubuntu icon and choose Gnome-fallback. That should take you to where you want to be. If that option isn't there, you'll need to install it.

Hope that helps. Welcome aboard!

---

### Post by thisislinuxdj on 2013-04-19
thanks. will try that gnome-fallback! think libdvdread4 is already installed will check. but might need to do second code you told me to do. will give you results. am building an linux based on 12.04 ubuntu so will come back if i run in to more problems! only major. building one for my school. thanks for reply!!!!!! :P

---

