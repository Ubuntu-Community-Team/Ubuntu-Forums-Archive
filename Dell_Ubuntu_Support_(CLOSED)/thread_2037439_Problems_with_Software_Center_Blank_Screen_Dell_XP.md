---
title: "Problems with Software Center Blank Screen Dell XPS 15 L502X"
date: 2012-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jonesyp on 2012-08-04
Hi,

I have a Dell XPS 15 L502X with Ubuntu 12.04 Desktop LTS and Nvidia GeForce GT525M.  I'm trying to buy a game from the software center, and after I enter my Launchpad login, I get a blank screen.  I have looked at similar reports, and they all seem to say this is now fixed.

I have also installed BumbleBee (Which supports the Nvidia Cards) and tried running software-center from the command line with or without the prefix of 'optirun'

This is the output from the console when using Bumblebee.

peter@amberley:~$ optirun software-center
2012-08-04 17:20:47,348 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-08-04 17:20:47,351 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-08-04 17:20:47,578 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-08-04 17:20:47,684 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-08-04 17:20:47,693 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2012-08-04 17:20:54,273 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2012-08-04 17:20:54,273 - softwarecenter.db.database - INFO - reopen() database
2012-08-04 17:20:54,274 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-08-04 17:21:30,994 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 137, '_get_opengl_vendor_renderer_version_tuple')'
2012-08-04 17:21:30,994 - debtagshw.opengl - INFO - gl vendor: NVIDIA Corporation
2012-08-04 17:21:30,995 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 138, '_get_opengl_vendor_renderer_version_tuple')'
2012-08-04 17:21:30,995 - debtagshw.opengl - INFO - gl renderer: GeForce GT 525M/PCIe/SSE2
2012-08-04 17:21:30,995 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 139, '_get_opengl_vendor_renderer_version_tuple')'
2012-08-04 17:21:30,995 - debtagshw.opengl - INFO - gl version: 4.2.0 NVIDIA 295.40

(software-center:2708): Gdk-WARNING **: software-center: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.


(software-center:2709): Gdk-WARNING **: software-center: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.


(software-center:2710): Gdk-WARNING **: software-center: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.


(software-center:2711): Gdk-WARNING **: software-center: Fatal IO error 11 (Resource temporarily unavailable) on X server :8.

** Message: console message:  @0: The page at about:blank displayed insecure content from [http://player.vimeo.com/video/41785069?title=0&byline=0&portrait=0](http://player.vimeo.com/video/41785069?title=0&byline=0&portrait=0).


** Message: console message:  @0: The page at [https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/](https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/) displayed insecure content from [http://b.vimeocdn.com/ts/289/605/289605396_295.jpg](http://b.vimeocdn.com/ts/289/605/289605396_295.jpg).


** Message: console message:  @0: The page at [https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/](https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/) displayed insecure content from [http://a.vimeocdn.com/p/1.4.22/fonts/vimeo.woff](http://a.vimeocdn.com/p/1.4.22/fonts/vimeo.woff).


** Message: console message:  @0: The page at [https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/](https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/) displayed insecure content from [http://a.vimeocdn.com/p/1.4.22/fonts/vimeo.ttf](http://a.vimeocdn.com/p/1.4.22/fonts/vimeo.ttf).


** Message: console message:  @0: The page at [https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/](https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/) displayed insecure content from [http://a.vimeocdn.com/p/1.4.22/fonts/vimeo.svg](http://a.vimeocdn.com/p/1.4.22/fonts/vimeo.svg).


** Message: console message:  @0: The page at [https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/](https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/) displayed insecure content from [http://b.vimeocdn.com/ts/289/605/289605396_640.jpg](http://b.vimeocdn.com/ts/289/605/289605396_640.jpg).


** Message: console message:  @0: The page at [https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/](https://myapps.developer.ubuntu.com/dev/apps/842/video/55082e5dfdccb4c0bf66f57cd94c43baaf09f01a/) displayed insecure content from [http://www.google-analytics.com/__utm.gif?utmwv=5.3.4&utms=1&utmn=1610361017&utmhn=player.vimeo.com&utmcs=UTF-8&utmsr=1366x768&utmvp=400x225&utmsc=24-bit&utmul=en-gb&utmje=1&utmfl=-&utmdt=Teaser%20Trailer%20-%20%22The%20Journey%20Down%3A%20Chapter%20One%22&utmhid=1737433084&utmr=-&utmp=%2Fvideo%2F41785069%3Ftitle%3D0%26byline%3D0%26portrait%3D0&utmac=UA-76641-35&utmcc=__utma%3D256147786.1984732692.1344097295.1344097295.1344097295.1%3B%2B__utmz%3D256147786.1344097295.1.1.utmcsr%3D(direct)%7Cutmccn%3D(direct)%7Cutmcmd%3D(none)%3B&utmu=qBAgAAAAAAAAAAAAQ~](http://www.google-analytics.com/__utm.gif?utmwv=5.3.4&utms=1&utmn=1610361017&utmhn=player.vimeo.com&utmcs=UTF-8&utmsr=1366x768&utmvp=400x225&utmsc=24-bit&utmul=en-gb&utmje=1&utmfl=-&utmdt=Teaser%20Trailer%20-%20%22The%20Journey%20Down%3A%20Chapter%20One%22&utmhid=1737433084&utmr=-&utmp=%2Fvideo%2F41785069%3Ftitle%3D0%26byline%3D0%26portrait%3D0&utmac=UA-76641-35&utmcc=__utma%3D256147786.1984732692.1344097295.1344097295.1344097295.1%3B%2B__utmz%3D256147786.1344097295.1.1.utmcsr%3D(direct)%7Cutmccn%3D(direct)%7Cutmcmd%3D(none)%3B&utmu=qBAgAAAAAAAAAAAAQ~).



Many thanks

Peter Jones

---

