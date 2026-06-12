---
title: "Nvidia Twinview - Desktop Goes Black"
date: 2008-01-31
forum: Desktop Environments
---

### Post by snanand on 2008-01-31
I successfully configured my two monitors using twinview through nvidia-settings. now, everytime i login, my desktop wallpaper is just back and the right click does not work. and nautilus does not work. other parts, such as the panel are working fine. any suggestions on what's going on?

thanks.

---

### Post by anachreon_ on 2008-02-01
Hi,

Your post is a little too vague to troubleshoot.  Generally a good idea to include more information : what displays are you using?  What are the resolutions?  Could you include your xorg.conf?  What kind of video card do you have?  What version of Ubuntu are you using?  Are you using Gnome or KDE?

---

### Post by snanand on 2008-02-02
ok, solved it. for some reason, setting up dual monitors through nvidia-settings messes up the permissions for nautilus. nautilus runs fine under sudo. so, i deleted the directories .gnome .gnome2 .gnome2_private and .nautilus and rebooted. nautilus and all desktop components run fine now. maybe a bug in nvidia-settings?

i'm using gutsy gibbon on gnome using the nvidia drivers.my graphics card is nvidia 7950gtx.

---

