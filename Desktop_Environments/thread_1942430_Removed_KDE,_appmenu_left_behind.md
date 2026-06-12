---
title: "Removed KDE, appmenu left behind?"
date: 2012-03-17
forum: Desktop Environments
---

### Post by Eskapism on 2012-03-17
Right so the first thing I did once I setup Ubuntu 11.10 on my laptop is installed GNOME3.
That was weeks ago, but today I installed KDE and within minutes of using it I decided to uninstall it.

I used this guide to install it: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
And used this guide to uninstall it: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
From that page, I entered the commands under 'Remove Kubuntu'.

Everything seemed fine, so I rebooted and logged in with GNOME.
On GNOME I use a transparent shell theme called Zukitwo so I removed the global appmenu so the theme worked right. But now that I've removed KDE, there's an appmenu or something behind the top bar? :(

[IMG]http://i.imgur.com/K4SJa.jpg[/IMG]
(top left)

I tried to remove it with ```
sudo apt-get remove appmenu-gtk indicator-applet-appmenu indicator-appmenu
``` but it remained there even after a restart. So I tried a reinstall + restart + remove but it did nothing.

Any idea what to do?

Thanks.

---

### Post by Eskapism on 2012-03-17
I solved my issue :)

I just realised that one thing wasn't being removed, I think it was the qt appmenu :P

```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```

---

