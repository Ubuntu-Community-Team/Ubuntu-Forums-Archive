---
title: "Add images to Screensaver timetunnel"
date: 2010-07-31
forum: Desktop Environments
---

### Post by raistlin_kell on 2010-07-31
Can someone please post steps on adding images to screensavers? I'm interested in adding images to Cosmos, Timetunnel and some others. 

Ubuntu 10.04 AMD64. Have added the xscreensaver-extra & gl packages. 
Tnx in advance.

---

### Post by Artemis3 on 2011-01-06
Just copy/rename/edit the text files at /usr/share/applications/screensavers

For instance i made a timetunnelwho.desktop:

```
[Desktop Entry]
Name=TimeTunnelWho
Exec=/usr/lib/xscreensaver/timetunnel -root -tardis /home/artemis3/timetunnel_images/tardis.xpm -head /home/artemis3/timetunnel_images/whohead1.xpm -marquee /home/artemis3/timetunnel_images/whologo.xpm
TryExec=/usr/lib/xscreensaver/timetunnel
Comment=Draws an animation similar to the opening and closing effects on the Dr. Who TV show. Written by Sean P. Brennan.
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;
```

Of course you have to provide the pretty pics, which in this case i found here: [http://www.zettix.com/Graphics/timetunnel/](http://www.zettix.com/Graphics/timetunnel/)

Just remember to leave the TryExec line alone...

---

