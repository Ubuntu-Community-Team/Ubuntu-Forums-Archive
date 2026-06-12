---
title: "Using Nautilus outside of Gnome"
date: 2004-12-12
forum: Desktop Environments
---

### Post by stwog on 2004-12-12
I've installed Ubuntu on an older computer with only 128mb of RAM and gnome was just a bit to slow for me (actually its a lot too slow), so I install XFCE 4.2 RC1. Its working great for me, but the filemanager that comes with XFCE isn't my favorite. I'd like to continue using Nautilus, but there are a few problems... 

1. The MIME types are lost when using Nautilus under XFCE. 
2. The Computer section doesn't work at all, and I can't open any of the devices

Does anyone know if there are any services that I need to start in order to get Nautilus behaving properly? I have a feeling that HAL might be to blame, so does anyone know how to shut that service down? 

I'm coming from a Slackware w/ Dropline Gnome system, so I'm still a little lost in Ubuntu.

Thanks,
Simon

---

### Post by adbak on 2004-12-12
I've heard about Rox ( [http://rox.sourceforge.net/phpwiki/](http://rox.sourceforge.net/phpwiki/) ) which I assume to be more lightweight than Gnome & KDE but more robust than XFce.  However, my assumptions probably aren't totally correct.

I have, though, heard good things about Rox's File Manager.  So perhaps you might wanna give that a try.

---

### Post by burlap on 2004-12-12
AFAIK, to have devices automounted without Gnome and to have them in Nautilus, you have to start gnome-volume-manager. There should be some kind of start-up script for XFCE (I haven't used this one) and you can put volume manager there:
```
gnome-volume-manager &
```
I am not sure why MIME types are lost (I have used nautilus in windowmaker and fluxbox and they did work (Gnome 2.4), but I usually had gnome-settings-daemon running).

And BTW - rox is really nice (much better than XFCE file manager), but I haven't seen it in any of Ubuntu's repositories (multiverse notwithstanding).

---

### Post by liquid boy on 2006-06-09
im pretty sure you can just run 'gnome-volume-manager' in xfce, then save session on exit, that way next time you start up xfce, gnome-volume-manager will start.

---

