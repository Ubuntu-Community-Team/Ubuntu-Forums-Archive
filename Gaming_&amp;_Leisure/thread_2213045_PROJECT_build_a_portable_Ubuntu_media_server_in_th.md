---
title: "PROJECT: build a portable Ubuntu media server in the style of &quot;Seagate Wireless Plus&quot;"
date: 2014-03-24
forum: Gaming &amp; Leisure
---

### Post by graystrickland on 2014-03-24
I am seeking suggestions on how I might build a portable Ubuntu media server (probably from a small notebook like an Asus EEE PC) to provide all the function of ***Seagate Wireless Plus*** or ****its predecessor, that ***Seagate GoFlex Satellite***. These are portable USB hard drives with onboard battery and a stripped-down computer running Linux and a WiFi access point. Once configured, it will create its own WiFi environment, serving files (by Samba, WebDAV, FTP, etc.). However, it does not have a screen or keyboard or any direct video out (HDMI, VGA, etc.). I realize that setting up Ubuntu to act as a fileserver is child's play. However, I have some other questions:

1. Can you setup Ubuntu to be a Wireless Access Point (creating an ad hoc network) that multiple devices can connect to? 

2. Can this Ubuntu device simultaneously (while creating an ad hoc network) connect to another wireless network? And pass internet connectivity through to the ad hoc clients? 

3. Same as above, but the Ubuntu device connects by wired ethernet to a network, then passes internet connectivity through to the ad hoc clients? 

The primary purpose of this device will be to serve (but not transcode) media files to various Android and iOS devices while in a car (thus, no internet) and in a vacation spot (possibly with hotel-provided internet connectivity). Granted, if you can join the Ubuntu box to a wireless network that has internet connectivity, you could do the same with the various Android and iOS devices. However, from an administrative perspective, it's easier to just let the Ubuntu box connect to the hotel network and the other devices only connect to the Ubuntu device (while receiving internet as a pass-through). That way I don't have to go to every kid's tablet and configure each one for the hotel WiFi. 

To be clear, I used to own *Seagate Satellite* and now own *Seagate Wireless Pl*. They're great devices, but you can't connect one to the hotel/cabin TV via HDMI (or otherwise). I want all of the function of the *Wireless Plus*, _plus_ the ability to watch video on the device itself or display movies on a connected TV. 

Any and all suggestions on how I might do this (or do it differently / better) will be greatly appreciated.

---

### Post by bookrt on 2014-03-24
Interesting idea. I am not sure how the Seagate devices work but it sounds like they basically have an internal wifi router/hub built in. I have never done this before, but this seems to describe the type of adhoc network you are trying to create:

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

I don't know about 2 & 3, but I kind of doubt it. You could get a portable travel router to accomplish this if it is really worth it.

For the media software, I believe Plex is what you are looking for and it can be installed through Ubuntu Software Center. You install Plex to your server and all your devices and as long as you can connect to your server you can view your content.

---

