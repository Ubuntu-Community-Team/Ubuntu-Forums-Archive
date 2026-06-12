---
title: "Ubuntu Compiz - Problems with fullscreen virtual desktop wine"
date: 2013-08-17
forum: Desktop Environments
---

### Post by Shadowbadger on 2013-08-17
Apologies if this is the incorrect board for this, I could not see a more suitable one.  I understand that support for wine itself will be outwith the scope of an Ubunto forum however it may be possible to resolve my issue with Ubunto knowledge or configuration.  I am running 13.04, just installed in the last couple of days.  I am using wine 1.4.1, managed by qtwine.

I watch the NFL online, using NFL GamePass, think NFL GameRewind if you are in the U.S, just that here in the U.K and other places, most games are live as well.  It is a subscription based video streaming service which uses flash.  I tried both Google Chrome and Firefox natively on Ubuntu but in fullscreen the sound is choppy and there is substantial screen tearing.  So, I installed wine and used winetricks to install Flash 11 before installing Firefox 23.0.1.  My system is an Intel i5-4670k and as I have not yet purchased a dedicated GPU I am using the Intel HD4600.  I have my main display, a 23" 1920x1080 Dell monitor connected using DVI and I have a 20" Toshiba 1360x768 TV connected using HDMI.  In terms of basic Ubuntu desktop use, both monitors are working fine.

Using Firefox under wine I get display glitches when I go fullscreen on the streaming video whilst not using a virtual desktop.  When I enable a virtual desktop in winecfg for my main monitor, without having the TV connected everything works great.  The whole screen goes blue and my Windows app (Firefox) appears in the screen and my Flash video streaming can be fullscreened 1920x1080 entirely with no performance problems.  When I plug in the TV however things start to get wierd.  Firstly I am no longer able to fullscreen on the primary monitor, the virtual desktop goes onto the TV, except most of it is outwith the screen bounds such that I can only see the top left portion of the virtual desktop.  It does go fullscreen though.

When I set my virtual desktop to 1360x768 (the resolution of the TV) then it opens on the TV but underneath the Ubuntu top bar and a title bar for the virtual desktop is also visible.  I have tried setting both the TV and the virtual desktop to 1280x720 and the same thing happens.

[IMG]http://shadowbadger.files.wordpress.com/2013/08/screenshot_tv.png[/IMG]

Now I can watch my streamed NFL like that, but I need to adjust the virtual desktop to say 1360x715 so that the bottom of the virtual desktop does not go out of bounds on the screen, I am left with the bars at the top though.  I tried setting my virtual desktop to 1 pixel higher and wider than the  TV resolution to see if it would go fullscreen like the 1920x1080 did but in that configuration, the windowed virtual desktop goes to the  primary display in draggable window.  I am not sure if the fact the displays have different resolutions is causing the problem but I cannot set them identically as the monitor does not give me the option of 1280x720 or 1360x768.

So:

Is there a way to remove the Ubuntu top bar on the second display only?  I found I could remove the launcher but not the bar.

Is there a way to remove the title bar of the wine virtual desktop?  I have tried both with and without "Allow window manager to control/decorate windows" in winecfg.

is there a way to make the virtual desktop go fullscreen on either the TV or primary monitor?

Thanks

---

