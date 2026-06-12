---
title: "Fluxbox question: How do I access the internet and how can I access my pen drive?"
date: 2009-02-05
forum: General Help
---

### Post by Rytron on 2009-02-05
Hi.
How do I access the internet and how can I access my pen drive in Fluxbox?
There is no problem accessing the internet in XFCE. I cant find a network manager in Fluxbox. Also I cant find the media folder.
Thanks.

---

### Post by m_duck on 2009-02-05
If you've started with an XFCE or GNOME install and put fluxbox over the top, you should have everything you need. I'm not overly familiar with fluxbox (I do use openbox though) but if you add the following to your fluxbox autostart file (~/.fluxbox/autostart maybe?) it should start both a network manager (nm-applet) and a volume mounting daemon```
nm-applet &
gnome-volume-manager &
```If you don't have either of these, you can install them with ```
sudo apt-get install network-manager-gnome gnome-volume-manager
```for network manager and the volume manager respectively.

If you started with XFCE, I think there is a way to use Thunar's volume management but I'm not sure how.

Some links I found which may be useful:
 - [thread=116759]General fluxbox stuff[/thread]
 - [thread=885693]Alternative fluxbox methods[/thread]

Hope this helps.

---

### Post by Rytron on 2009-02-06
Thank you m_duck.

---

