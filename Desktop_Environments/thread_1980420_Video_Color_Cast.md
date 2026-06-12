---
title: "Video Color Cast"
date: 2012-05-15
forum: Desktop Environments
---

### Post by hartz on 2012-05-15
I understand from [googling]("http://lmgtfy.com/?q=Ubuntu+video+playback+blue+green+color+tinted") that there is a solution to my problem:  Use gstreamer-properties to set the following:

```
videobalance hue=-1 ! autovideosink
```

This should fix the swapped colors / blue skin issue in video playback(which, I understand, is caused by a combination of the Flash player and/or nvidia driver.

Being a KDE user I don't have gstreamer-properties though.  Some searching revealed that it is included in the "gnome-media" package and it seems this package provides a pannel-applet for gstreamer properties.

Furthermore some "posts" hints that this should be fixable via the nvidia X-server settings.  I've narrowed it down to the X Server XVideo playback settings under the relevant "Screen" section.  There is a "Hue" slider which goes from -1000 to +1000

In photography hue really goes from -180 to +180 on the color wheel, with the prime colors equally spread out, separated by 120 degrees.  I suspect the gstreamer property referenced in numerous posts translates to either a 180-degree swap, or to a shift-by-one through the color wheel, eg 120 degrees.

So what value, between -1000 and +1000, does the "hue=-1" gstreamer property / adjustment map to?  And do I need to reboot or restart the X server?  How do I make this setting "stick"?

I would prefer a KDE native solution if there is one.  A Plasma gstreamer properties applet? Any other interfaces to gstreamer properties, eg config files, perl, python?  Environment variable settings to affect gstreamer/ffmpeg/friends? A gstreamer plugin for KDE system settings? Any other ideas?

Thanx!

---

### Post by hartz on 2012-05-16
I found that in VLC I can fix the shifted Hue issue, at least temporarily:

On the menu select Tools -> Effects and Filters -> Video Effects -> Essential.

Check to enable the "Image Adjust" checkbox to make the Hue slider available. Moving the slider have an immediate / live effect on any video playing in the background.

I'm not sure that this setting sticks: it may be dependant on what file is playing, or what codec it uses, or whether any file is playing, and I think the setting got reset last night with an update.  In my testing the setting did get "remembered" when I closed and then re-opened the same file, but got reset after I rebooted after updates.

I'm not particularly happy with the situation - Flash and other players are still affected, and while I don't use the other video players today, I might change my mind about that at any time when another player becomes the best tool for the job.

So I am still looking for a KDE native way to access gstreamer "properties".

---

### Post by hartz on 2012-05-16
I've highlighted some of the more-offensive dependancies of gnome-media.  You may have more - I have a few gnome applications that I can't live without.

Some of these are truly mind boggling though, eg "apg" and gnome online account support????


```
~$ sudo apt-get install gnome-media
[sudo] password for johan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apg gnome-control-center gnome-control-center-data gnome-menus gnome-online-accounts
  gnome-session-bin gnome-user-guide gstreamer0.10-gconf indicator-power indicator-sound
  libgnome-control-center1 libgnome-media-profiles-3.0-0 libgnome-menu-3-0 libgoa-1.0-0
  libgoa-1.0-common libgtop2-7 libgtop2-common libido3-0.1-0 libjson-glib-1.0-0 libnm-gtk-common
  libnm-gtk0 librest-0.7-0 libyelp0 mousetweaks ubuntu-docs ubuntu-system-service yelp yelp-xsl
Suggested packages:
  gnome-screensaver xscreensaver libcanberra-gtk-module network-manager-openvpn-gnome
  network-manager-vpnc-gnome network-manager-pptp-gnome gnome-bluetooth ttf-dejavu
The following NEW packages will be installed:
  apg **gnome-control-center** gnome-control-center-data gnome-media **gnome-menus** gnome-online-accounts
  **gnome-session-bin** gnome-user-guide gstreamer0.10-gconf indicator-power indicator-sound
  libgnome-control-center1 libgnome-media-profiles-3.0-0 **libgnome-menu-3-0** **libgoa-1.0-0**
  libgoa-1.0-common libgtop2-7 libgtop2-common libido3-0.1-0 libjson-glib-1.0-0 libnm-gtk-common
  libnm-gtk0 librest-0.7-0 libyelp0 **mousetweaks** ubuntu-docs ubuntu-system-service yelp yelp-xsl
0 upgraded, 29 newly installed, 0 to remove and 12 not upgraded.
Need to get 6*920 kB of archives.
After this operation, 79,8 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by hartz on 2012-05-18
Bump - does anybody know of a KDE native way to access gstreamper properties?

I can't possibly be the only person with this issue...

---

