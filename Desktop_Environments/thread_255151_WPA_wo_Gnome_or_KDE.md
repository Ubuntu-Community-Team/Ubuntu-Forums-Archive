---
title: "WPA w/o Gnome or KDE"
date: 2006-09-11
forum: Desktop Environments
---

### Post by petersok on 2006-09-11
My main goal is to get wireless working with WPA on my latop (w/ a IPW 2100 wireless ethernet controller).  While it sounds like network-manager provides this without a hitch for most people, I am not running gnome or kde.  So I figure my best route is to use wpa-supplicant.

I am following the [how to on the wiki]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") without luck.  Here is the output when I run wpa_supplicant:

ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption
Trying to associate with [MACADDRESS} (SSID="essid" freq=0 MHz)
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Authentication with [MACADDRESS] timed out.

I was unable to find mention of anything like this on forums.  I did notice that the mac address specified by the output had a different final digit then the one listed on my routers web interface.  Could this be significant?  Thanks for any help from anyone who remembers using WPA supplicant...

P.S. Is there any way to make use of network-manager without one of the two main window managers?  I am currently using ratpoison...

---

