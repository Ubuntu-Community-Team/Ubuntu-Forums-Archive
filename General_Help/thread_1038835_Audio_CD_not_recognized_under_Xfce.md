---
title: "Audio CD not recognized under Xfce"
date: 2009-01-13
forum: General Help
---

### Post by whshao on 2009-01-13
I have a default desktop ubuntu 8.10 install, and I also put Xfce as a secondary window manager. My audio CDs can be recognized automatically in rhythmbox and sound-juicer under Gnome, but they cannot even be recognized even after scanning for removable media in rhythmbox under Xfce.

Is there's a service that I need to start, or if there's a command that I need to run to mount the audio CD? Data CDs are mounted under Xfce as soon as I insert them. And I already checked the "Launch Gnome services on startup" checkbox under the Xfce "Sessions and Startup" item, "Advanced" tab.

Thanks in advance.

---

### Post by whshao on 2009-01-15
Problem solved. I found out that Thunar can handle it. It showed up on the left side pane, and when I right-clicked on the Audio CD icon, I can hit "Open". The wav tracks are shown, and a button allows me to use Rhythmbox to play the CD.

---

### Post by Bucky Ball on 2009-01-15
Yea, xfce has a few different ways of going about things, but I love it! You might try Applications->Settings->Settings Manager->Removable Drives and make sure it is checked to mount the media.

Also, Applications->Settings->Settings Manager->Desktop and down the bottom, make sure 'removable devices' is checked.

---

### Post by whshao on 2009-01-15
Sorry, I conveyed one piece of misinformation. It wasn't Thunar that showed the mounted audio CD on the left side, it was Nautilus.

One other way that I found out is to install the package xfce4-cddrive-plugin, and add that plug-in to the panel. However, the size of that plug-in icon is somewhat tricky, as it would take up a lot of empty horizontal space on the left side, and I don't think that is easily configurable. That is why the placement of the icon is essential. I put it to the right of my icon box because the opened application icons, when you have a bunch of them, have no problem stretching into the CD Drive plug-in territory, unlike other icons.

---

