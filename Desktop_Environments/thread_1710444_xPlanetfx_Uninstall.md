---
title: "xPlanetfx Uninstall???"
date: 2011-03-19
forum: Desktop Environments
---

### Post by xXDarkRoninXx on 2011-03-19
Ok so I installed xPlanet on my Ubuntu 10.10 because I thought it was cool. Once I realized that every time that I restarted my computer that it would default to xPlanet (even when I changed my background before shutdown), I wanted to get rid of it. I went to the Ubuntu Software center and removed xplanet and xplanet-images then restarted my computer. The program is gone but the desktop still showing xPlanet as the default background when Ubuntu starts, and the background looks corrupted and screwed up. What do I do?

In a nutshell:
I want to get rid of xPlanet as the default background.

---

### Post by ankspo71 on 2011-03-20
Hi,
It has been a long time since I have used Xplanetfx, and since then I have moved away from Gnome, so I might not be much help now, but I remember XplanetFX having a daemon that runs in the background that sets the background as the latest generated xplanet image. For some reason, that daemon didn't get uninstalled and is still running on your system. I think this is what is stopping you from choosing a different wallpaper.

Did you uninstall all packages belonging to xplanetfx? (eg: xplanetfx, xplanet and xplanet-images). If you installed XplanetFX as a *.deb file (like the one available at Gnome-look.org or [http://mein-neues-blog.de/xplanetFX/#install](http://mein-neues-blog.de/xplanetFX/#install)), you will be able to uninstall "xplanetfx" by using Synaptic Package Manger. If you used a binary/source package to install it (like a *.tar.gz file), then you will need to uninstall the remaining bits from your system manually.

Also, check to see if there is a start up entry for xplanetfx in the "StartUp Applications" application, located in your system menu. If there is one present for xplanetfx, delete it or disable it.

Hope this helps.

---

### Post by ankspo71 on 2011-03-20
Hi Again,
The removal instructions can be found here:
[http://mein-neues-blog.de/xplanetFX/#install](http://mein-neues-blog.de/xplanetFX/#install)
It is farther below the installation instructions, so keep scrolling down until you see it.

---

