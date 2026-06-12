---
title: "flash in firefox"
date: 2009-06-03
forum: General Help
---

### Post by Billko on 2009-06-03
I have installed the flashplayer plugin  and about plugins shows I have       File name: libflashplayer.so      Shockwave Flash 10.0 r22    with shockwave-flash   and application/futuresplash  enabled.    Yet Flash films do not play for me and I get the warning:  Video Player undefined for this type of media (check Tools menu, MediaPlayerConnectivity...) application/x-shockwave-flash    When I open the configure dialog there the Flash media type has an empty text box alongside it and a browse button.  What file should I be selecting when I browse?

---

### Post by gawadelnil2002 on 2009-06-03
> **Billko said:**
> I have installed the flashplayer plugin  and about plugins shows I have       File name: libflashplayer.so      Shockwave Flash 10.0 r22    with shockwave-flash   and application/futuresplash  enabled.    Yet Flash films do not play for me and I get the warning:  Video Player undefined for this type of media (check Tools menu, MediaPlayerConnectivity...) application/x-shockwave-flash    When I open the configure dialog there the Flash media type has an empty text box alongside it and a browse button.  What file should I be selecting when I browse?
Try to get adobe flash installer for adobe website itself , that happened for me before that installed nonfree-flash-plugins and nothing worked for me when i open youtube it tells me get the latest adobe flash player and i clicked the link i downloaded the debian file for ubuntu and i installed and the flash worked after that , here is the link [http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)

---

### Post by albinootje on 2009-06-03
> **Billko said:**
> I get the warning:  Video Player undefined for this type of media (check Tools menu, MediaPlayerConnectivity...) 

Does it work when you temp. disable the MediaPlayerConnectivity addon and restart Firefox ?
And is it possible to make an exception for flash within the preferences of this addon ?

---

### Post by Billko on 2009-06-04
> **gawadelnil2002 said:**
> Try to get adobe flash installer for adobe website itself , that happened for me before that installed nonfree-flash-plugins and nothing worked for me when i open youtube it tells me get the latest adobe flash player and i clicked the link i downloaded the debian file for ubuntu and i installed and the flash worked after that , here is the link [http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)

 Thanks a lot.  That has fixed it !

---

### Post by mr PUG on 2009-06-04
this fixed the flash playback problem for me" (ubuntu jaunty 9.04)

```
$ sudo apt-get remove --purge flashplugin-*
$ sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
$ sudo apt-get install flashplugin-nonfree
```

---

### Post by mr PUG on 2009-06-04
this fixed the flash playback problem for me"

```
$ sudo apt-get remove --purge flashplugin-*
$ sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
$ sudo apt-get install flashplugin-nonfree
```

---

