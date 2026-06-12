---
title: "Compiz Enhanced zoom desktop for dual displays"
date: 2012-07-27
forum: Desktop Environments
---

### Post by kroken on 2012-07-27
Hello, everyone. 

I have installed Ubuntu 12.04 today, and I'm trying to set up screen magnification to work the way I want it to. I have a dual display setup. In Windows 7 I have used the Magnifier application, and made a docked magnifier stretched over one full monitor. The other monitor displays a normal view, and the docked magnifier displays the area around the cursor. This is a setup that works very well for me, and I would like to replicate it in Ubuntu. Here is a screenshot which hopefully shows my setup clearly:
[[img]http://bildr.no/thumb/1238143.jpeg[/img]](http://bildr.no/view/1238143)

In the screenshot, the mouse cursor is not displayed on the left (normal view) monitor. This is a Windows bug, it is in fact above the search button, as seen in the magnified view on the right monitor.

I have installed Ubuntu 12.04 from the live CD, and I'm using the default Unity desktop. Ubuntu mirrors the two displays by default, I have disabled this so it behaves like one extended desktop. I have installed the compizconfig-settings-manager package, and enabled the Enhanced zoom desktop plugin.

The problem is that Compiz will only magnify a window on the display that window is on. If I put an application window on display #1, I can use the zoom in key to get a magnified view on display #1, as if I was running full-screen magnification on a single display setup. I can drop an application window on display #2 and zoom in on this to get a magnified view of it on display #2. I can run magnified views on both display #1 and #2 at the same time, but they will only view the windows that are on their respective display. What I *cannot* do, is have the application window on display #1 and the magnified view of that application window on display #2. This is what I want to achieve, and I hope someone has an idea on how it can be done. I am not restricted to using Compiz for this task, but it seems to be the application that can get closest to what I want. I will gladly take suggestions for other magnifiers that are able to do this, as long as they also have focus tracking.

My graphics card is an AMD Radeon HD5770, and I am using the free driver (the one chosen by the installer). I have not yet tried the proprietary driver, as I believe it will mainly resolve performance issues. Please let me know if you need any additional information, and how I can find this information.

I wish everyone a pleasant weekend, and I am grateful for any suggestions. :)

---

### Post by kroken on 2012-07-29
A small update.

I still haven't come any further with Unity/Compiz. I have now installed xubuntu-desktop and kubuntu-desktop packages, as well as Cinnamon 1.4. The MATE desktop repository is currently down, so I haven't got that yet. 

Cinnamon doesn't seem to have any magnifier, I could not find one in XFCE either. With KDE I can create my desired setup easily with KMag, but it lacks any kind of focus tracking. Interestingly, there seems to be [a GSoC project](http://amanonit.blogspot.no/2012/06/gsoc-focus-tracking-working-in-kwin.html) for this. I will have to keep an eye on future KDE releases.

I will try MATE when their repo is up again. In the meantime, I am happy for any suggestions for desktop environment and window manager or magnifier application to create a setup usable for me. :)

---

